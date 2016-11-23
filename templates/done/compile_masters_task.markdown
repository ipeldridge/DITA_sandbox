
## Install a compile master

The following provides instructions for installing a compile master.

Before you begin:

Review these procedures before beginning, as performing these steps out of order can cause problems for your configurations. In addition, note the following about these steps:

- It's assumed you've already installed a [split](./install_pe_split.html) or [monolithic](./install_pe_mono.html) PE deployment.
- It’s assumed all servers are running the same OS and architecture.
- In these procedures, the following hostnames are used, but you will need to replace them to match the hostnames in your infrastructure:
   - **Puppet master/CA server (MoM)**: `MASTER.EXAMPLE.COM`.
   - **PE console**: `CONSOLE.EXAMPLE.COM`.
   - **PuppetDB**: `PUPPETDB.EXAMPLE.COM`.
   - **Compile master**: `COMPILE.MASTER.EXAMPLE.COM`.
- The machine that will become your compile master should NOT already have a Puppet agent installed.


1. SSH into `COMPILE.MASTER.EXAMPLE.COM` and run the following command:

   ~~~
   `curl -k https://<MASTER.EXAMPLE.COM>:8140/packages/current/install.bash | sudo bash -s main:dns_alt_names=<COMMA-SEPARATED LIST OF ALT NAMES FOR THE PUPPET MASTER>`
   ~~~
   
   >**Note:** The `dns_alt_names` value should be set to a comma-separated list of any alternative names that may be used by Puppet agents to connect to the master. The installation uses "puppet" by default.
   
   This installs and configures the Puppet agent on `COMPILE.MASTER.EXAMPLE.COM`.
   
2. From the command line of `MASTER.EXAMPLE.COM`, run `puppet cert --allow-dns-alt-names sign add.master.example.com`.

   >**Note**: You cannot use the console to sign certs for nodes with DNS alt names.
   
3. From the command line on `COMPILE.MASTER.EXAMPLE.COM`, run `puppet agent -t`.

4. Use the PE console to classify `COMPILE.MASTER.EXAMPLE.COM` so that it can function as a Puppet master and proxy requests to the PE certificate authority.

   a. In the console, click **Nodes** > **Classification**, and in the **PE Infrastructure** node group, select the **PE Master** node group.
   
   b. From the __Certname__ section, in the __Node name__ field, enter `COMPILE.MASTER.EXAMPLE.COM`.
   
   c. Click __Pin node__, and commit changes.
   
   >**Tip**: See [Using load balancers with compile masters](./install_lei_load.html) for more information about configuring `pe_repo` to point at your load balancer for agent installation requests.
   
5. (Optional) Configure `pe_repo` to send agent install requests to the load balancer

   >**Note:** If you're using load balancers, in this task, you configure `pe_repo` so agent installation requests will be sent to the load balancer.

   a. From the console, click __Nodes__ > __Classification__, and select the __PE Master__ group.
   
   b. In the __PE Master__ group, click the __Classes__ tab, and find the __pe_repo__ class.
   
   c. From the __Parameter__ drop-down list, select __master__.
   
   d. In the __Value__ field, enter the address your load balancer resolves to (for example, `LOADBALANCER.EXAMPLE.COM`).
   
   e. Click __Add parameter__ and then the __Commit change__ button.

6. Run Puppet on selected nodes. 

   >**Important**: The following Puppet runs **MUST** be done in the order listed in the following choices. Puppet has to be run on these nodes in this order for the compile master to be active as quickly as possible. 

   - **For a monolithic installation:**
      1. `COMPILE.MASTER.EXAMPLE.COM`
      2. `MASTER.EXAMPLE.COM`
    
   - **For a split installation:**
      1. `COMPILE.MASTER.EXAMPLE.COM`
      2. `PUPPETDB.EXAMPLE.COM`
      3. `CONSOLE.EXAMPLE.COM`
      4. `MASTER.EXAMPLE.COM`

   In both cases, you must wait for the run to finish on the the first node before moving on to the next.


* * *
