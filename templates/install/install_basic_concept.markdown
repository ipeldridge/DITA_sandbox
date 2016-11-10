<!--Concepts provide context for task and reference topics. -->

## Installing Puppet Enterprise: Overview

Your PE installation will go more smoothly if you know a few things in advance.

Puppet Enterprise's functions are spread across several different components which get installed and configured when you run the installer. You can choose to install multiple components on a single node (a "monolithic install") or spread the components across multiple nodes (a "split install"), but you should note that the "agent" component gets installed on every node.

You should decide on your deployment needs before starting the install process. For each node where you'll install a PE component, you should know the fully qualified domain name where that node can be reached and you should ensure that firewall rules are set up to allow access to the [required ports](./sys_req_sysconfig.html#firewall-configuration).

With that knowledge in hand, the installation process will proceed in **three stages**:

1. You choose an installation method.

2. You install the main components of PE---the Puppet master, PuppetDB (and database support), and the PE console.

3. You install the Puppet agent on all the nodes you wish to manage with PE. Refer to the [agent installation instructions](./install_agents.html).

### Choosing an installation method

Before you begin, choose an installation method. We've provided a few paths to choose from, and provided links to the corresponding installation instructions.

   * [Web-based monolithic installation](./install_pe_mono.html): The base install type for a [standard monolithic installation](./sys_req_hw.html#monolithic-installation) or a [monolithic plus compile masters installation](./sys_req_hw.html#monolithic-plus-compile-masters-installation). 

    * [Text-mode installation](./install_text_mode.html): Use the example `pe.conf` file provided in the PE installation tarball or create your own to install PE. Refer to the text-mode installation overview for more information about this installation mode. With text-mode, you can create a split or monolithic installation. 

See the [system requirements](./sys_req_hw.html) for additional hardware-related specifications.

>**Tip:** Before beginning installation, you should familiarize yourself with the services and components that make up PE.
>
>See the [PE architecture overview](./pe_architecture_overview.html) for more information.


* * *
