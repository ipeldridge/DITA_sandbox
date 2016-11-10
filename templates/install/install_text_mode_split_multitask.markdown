<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Text-mode installation: split

The following instructions are for performing a text mode split installation of PE. This installs the Puppet master, the PE console, and PuppetDB components on three separate machines---one machine for each component.

Before beginning:

- Review [the text mode installation overview](./install_text_mode.html)
- [Download and verify the appropriate PE tarball](./install_basic.html#downloading-puppet-enterprise).

Perform the following steps in the order given.

### Install the Puppet master

In this task, you install the Puppet master.

1. Unpack the tarball by running `tar -xf <TARBALL_FILENAME>`. This requires about 1 GB of space in `/tmp`.
2. From the installer directory, run the installer. The installation steps will vary depending on the path you choose.

   * To have the installer open a copy of `pe.conf` for you to edit and install with, run the installer **without the `-c` flag**.

     ~~~
     sudo ./puppet-enterprise-installer
     ~~~
      
   * To use a `pe.conf` file that you've previously populated, run the installer **with the `-c` flag** pointed at the `pe.conf` file.

     ~~~
     sudo ./puppet-enterprise-installer -c <FULL PATH TO pe.conf>
     ~~~
     
     >**Warning:** If you're using a pre-populated file, be sure you've set the parameters correctly as detailed in the following steps.
  
3. If you ran the installer **without the -c flag**, select "text-mode" when prompted. 

   This opens your text editor with a `pe.conf` file that you can edit to match your infrastructure and add any additional text-mode installation options as needed. 

4. Set the following parameters:

   - `"console_admin_password": "<PASSWORD>"`— The password used to log into the PE console      
   - `"puppet_enterprise::puppet_master_host": "<FQDN>"`— The FQDN of the node hosting the Puppet master
   - `"puppet_enterprise::console_host": "<FQDN>"`— The FQDN of the node hosting the PE console
   - `"puppet_enterprise::puppetdb_host": "<FQDN>"`— The FQDN of the node hosting PuppetDB
      
    >**Warning**: In a split install, do not use the "%{::trusted.certname}" value for the Puppet master. 
      
5. If you have an external PostgreSQL server, refer to the [external PostgreSQL parameters in the pe.conf reference](./install_pe_conf_param.html#external-postgresql-parameters) and add them to `pe.conf`.
 
6. Save and close the file.

   This starts the installation.
   
7. When the installation completes, install PuppetDB.


### Install PuppetDB

In this task, install PuppetDB.

1. Transfer the PE installer tarball and the `pe.conf` file to the PuppetDB node.
2. Unpack the tarball by running `tar -xf <TARBALL_FILENAME>`. This requires about 1 GB of space in `/tmp`.
3. If the `pe.conf` parameter `puppet_enterprise::puppet_master_host` is set to `"%{::trusted.certname}"`, change the value to the FQDN of the Puppet master.
4. From the installer directory, run the installer with `sudo ./puppet-enterprise-installer -c <FULL PATH TO pe.conf>`.
5. When the installation completes, continue to install the PE console.

### Install the PE console

In this task, install the PE console.

1. Transfer the PE installer tarball and the `pe.conf` file to the PE console node.
2. Unpack the tarball by running `tar -xf <TARBALL_FILENAME>`. This requires about 1 GB of space in `/tmp`.
3. If the `pe.conf` parameter `puppet_enterprise::puppet_master_host` is set to `"%{::trusted.certname}"`, change the value to the FQDN of the Puppet master.
4. From the installer directory, run the installer with `sudo ./puppet-enterprise-installer -c <FULL PATH TO pe.conf>`.
5. When the installation completes, continue to run Puppet on all split nodes.

### Run Puppet on all split nodes

To complete the split installation, run Puppet on all nodes in the split installation in the order given.

1. Run Puppet on the Puppet master node.
2. Run Puppet on the PuppetDB node.
3. Run Puppet on the PE console node.



1. <# IMPERATIVE COMMAND #>


<!--Insert additional tasks as needed.-->