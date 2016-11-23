<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Uninstalling PE from agent nodes

The following steps explain how to uninstall PE agents from *nix nodes.

When you install agent nodes using the [agent installation script](./install_agents.html), PE does not include the `puppet-enterprise-uninstaller` script as part of the agent package. There are a few additional steps you'll need to take to uninstall PE from agent nodes.

> **Note:** About Mac OS X and Windows agent uninstallation
>
> For instructions on uninstalling PE on nodes running Windows, refer to the [uninstalling section](./install_windows.html#uninstalling) of the Windows agent installation instructions.
>
> To uninstall PE on a node running Mac OS X, simply access the uninstaller .pkg in the original OS X PE agent package you downloaded, and follow the instructions in the uninstall dialog. When you use the OS X uninstaller, you will completely remove all aspects of the PE agent from that node.

1. **On your Puppet master**, navigate to `/opt/puppetlabs/bin/` and copy `puppet-enterprise-uninstaller` to the agent node you're uninstalling PE from.
2. Still your Puppet master, navigate to `/opt/puppetlabs/server/share/installer/` and copy `utilities` to the agent node you're uninstalling PE from.
3. **On the agent node**, run sudo `./puppet-enterprise-uninstaller`, and follow the prompts.

   You do not need to run the `utilities` script to uninstall PE---it just needs to be present in the same directory as the uninstaller.

4. (**Optional**) If you plan to reinstall PE on that node at a later date, remove the agent certificate for the agent from the Puppet master. On the Puppet master, run the following command:

   ~~~
   puppet cert clean <AGENT CERT NAME>
   ~~~


* * *
