<!--Multi-tasks can be used to introduce a process where each child task is required, or to group a set of similar tasks.-->

## Installing Puppet agents with PE package management

The following instructions explain how to use PE package management to install Puppet agents in a PE infrastructure. You can install agents that have the same OS and architecture as the Puppet master or that have a different OS and architecture than the Puppet master. 

You can install agents that have the same OS and architecture as the Puppet master or that have a different OS and architecture than the Puppet master. 

Before you begin, please note the following about these instructions:

- The `<PUPPET MASTER HOSTNAME>` portion of the installer script---as provided in the following examples---refers to the FQDN of the Puppet master. If you've already logged into the console, you can find the exact script with the correct Puppet master hostname for your installation by clicking on **node requests** in the top right-hand corner of the console. (You do not need to have pending node requests to click.)

>**Tip:** If you can't use `curl -k` to install agents as shown in the following procedures, refer to the [instructions on using `curl` against the Puppet master CA cert](#optional-install-agents-without-curl-k).

### Install agents with same same OS and architecture as the Puppet master

If your Puppet master and agent have the same OS and architecture, there is no additional configuration to perform.  

1. SSH into the node where you want to install the PE agent, and run the following command:

   ~~~
   curl -k https://<PUPPET MASTER HOSTNAME>:8140/packages/current/install.bash | sudo bash`
   ~~~

   >**Tip*:* See [passing configuration parameters to the install script](#passing-configuration-parameters-to-the-install-script) to specify configuration settings, such as specifying a cert name, which will be added to `puppet.conf`.

2. After the installation completes, [sign the agent certificates](#signing-agent-certificates).

### Install agents with a different OS and architecture than the Puppet master

To install an agent with a different OS than the Puppet master, you add the appropriate class for the repo that contains the agent packages and then classify the PE Master node group with that class. You then run the install script from the agent to retrieve the necessary packages for installation. 

In the following example, the Puppet master is on a node running RHEL 6 and the agent is on a node running Debian 6 on AMD64 hardware.

> **Note**: If your Puppet master uses a proxy server to access the internet, refer to [this known issue](./release_notes_known_issues_install.html#install-agents-with-different-os-when-puppet-master-is-behind-a-proxy) for a workaround.

1. 1. In the console, click **Nodes** > **Classification**, and in the **PE Infrastructure** group, select the **PE Masters** group.

2. On the **Classes** tab in the **Class name** field, enter `pe_repo` and select the repo class from the list of classes.

   >**Note**: the repo classes are listed as `pe_repo::platform::<AGENT_OS_VERSION_ARCHITECTURE>`

3. Click **Add class**, and commit changes.

4. Run `puppet agent -t` to configure the Puppet master node using the newly assigned class.

   The new repo is created in `/opt/puppetlabs/server/data/packages/public/<PE VERSION>/<PLATFORM>/`.

5. SSH into the Debian node where you want to install the agent, and run `curl -k https://<PUPPET MASTER HOSTNAME>:8140/packages/current/install.bash | sudo bash`.

    The script will install the PE agent packages, create a basic `puppet.conf`, and kick off a Puppet run.

   >**Tip**: see [Passing Configuration Parameters to the Install Script](#passing-configuration-parameters-to-the-install-script) to specify configuration settings, such as specifying a cert name, which will be added to `puppet.conf`.

6. After the installation completes, [sign the agent certificates](#signing-agent-certificates).

* * *