<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Installing agents in a Puppet Enterprise infrastructure without internet access

If your PE infrastructure does not have access to the internet beyond your infrastructure, you will not be able to fully use the agent installation instructions, as your Puppet master does not have access to PE's agent package distribution repo. Instead you can download the appropriate agent package, and then use one of the following options that best corresponds to your deployment needs.

Before beginning, [download the appropriate agent package](http://puppetlabs.com/misc/pe-files/agent-downloads). 

### Use PE package management

The following instructions are for using PE package management to install agents when you don't have internet access beyond your infrastructure.

1. Copy the agent package into the `/opt/puppetlabs/server/data/staging/pe_repo-<PUPPET AGENT VERSION>` directory on your Puppet master.

2. Follow the steps in [Installing puppet agents with pe package management](#installing-puppet-agents-with-pe-package-management) to complete the process.

>**Note:** You must perform these steps any time you upgrade your Puppet master. 

### Use your own package management

The following instructions are for using your own package management to install agents when you don't have internet access beyond your infrastructure.

1. Add the agent package to your own package management/distribution system.
2. Use the PE console to disable the PE-hosted repo. 

   a. In the console, click **Nodes** > **Classification** and in the **PE Infrastructure** group, select the **PE Master** group. 
   
   b. On the **Classes** tab, find `pe_repo` class (as well as any class that begins `pe_repo::`), and click **Remove this class**. 
   
   c. Commit changes. 
   
>**Note:** You must perform these steps any time you upgrade your Puppet master. 

### Set compile masters to install agents from your own package management

If your infrastructure relies on compile masters to install agents, you don’t have to copy the agent package to each compile master. Instead, use the PE console to specify a path to the agent package on your package management server.

1. Add the agent package to your own package management/distribution system.
2. Set the `base_path` parameter of the `pe_repo` class to your package management server. 

   a. In the console, click **Nodes** > **Classification** and in the **PE Infrastructure** group, select the **PE Master** group.
   
   b. On the **Classes** tab, find `pe_repo` class and specify the parameter:
   
      - **Parameter** -- Select **base_path**.
      
      - **Value** -- Enter the fully qualified domain name of your package management server. 
         
   c. Click **Add parameter** and commit changes. 

* * *
