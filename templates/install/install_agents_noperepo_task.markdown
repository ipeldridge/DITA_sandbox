<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Installing agents with your own package management

If you use your own package management tools, use the following steps to install PE agents.

Agent packages can be found on the Puppet master in `/opt/puppetlabs/server/data/packages/public/<PE VERSION>/`. This directory contains the platform specific repository file structure for agent packages. By default this will contain a repository matching your Puppet master's OS/architecture. For example, if your Puppet master is running on CentOS 7, in `/opt/puppetlabs/server/data/packages/public/<PE VERSION>/`, you will find the directory `el-7-x86_64`, which contains the directories with all the packages needed to install an agent.

If your nodes are running an OS and/or architecture that is different from the master, [download the appropriate agent package](http://puppetlabs.com/misc/pe-files/agent-downloads), extract the agent packages into the appropriate repo, and then install the agents on your nodes just as you would any other package (e.g., `yum install puppet-agent`).

Before you begin, [download the appropriate agent package](http://puppetlabs.com/misc/pe-files/agent-downloads).


1. Add the agent package to your package management repo. 

2. Configure the package manager on your agent node (Yum, Apt) to point to that repo.

3. Install the Puppet agent. 

   a. On Yum-based systems, run `sudo yum install puppet-agent`.
   
   b. On Apt-based systems, run `sudo apt-get install puppet-agent`.
   
4. Configure the agent using `puppet config set`. See [Configuring agents](#configuring-agents).




* * *
