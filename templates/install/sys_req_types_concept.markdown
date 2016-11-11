<!--Concepts provide context for task and reference topics. -->

## Choosing a Puppet Enterprise Architecture

There are two architecture types to choose from for your PE installation.

- [Monolithic installation](./install_pe_mono.html): the Puppet master, the PE console, and PuppetDB (with PostgreSQL) are all installed on one node. Because all components are on one node, this installation type is easier to install, upgrade, and troubleshoot. You can expand this installation type by adding compile masters to it.
- [Split installation](./install_tex_mode_split.html): the Puppet master, the PE console, and PuppetDB (with PostgreSQL) are each installed on separate nodes. You should only use this installation type if you have a limit on the number of cores per server you can have, or if you are running 8,000+ nodes.

A monolithic installation is the recommended, default installation type. A monolithic installation is appropriate for managing up to 2000 nodes. As you approach this number of managed nodes, you can scale your installation by [adding compile masters](./install_multimaster.html). Each compile master will allow you to manage approximately another 1500 nodes in your infrastructure, and you can continue adding compile masters until it starts causing performance degradation with PuppetDB or the PE console. Such performance issues typically occur around 8000 nodes. 

As your deployment grows, your path will likely go something like this:

1. You’ll install a monolithic installation on one node for managing tens to hundreds of nodes.
2. As you expand and bring more nodes under PE management, you’ll increase the resources available to your monolithic installation by providing more CPUs and RAM.
3. As you expand into managing thousands of nodes, you’ll add compile masters to distribute the agent catalog compilation workload.  You’ll likely reach a steady state if you’re managing less than 8000 nodes.
4. If your deployment grows even larger, you’ll migrate from a monolithic installation to a Large Environment Installation.

* * *
