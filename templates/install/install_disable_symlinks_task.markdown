<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Disabling Puppet Enterprise symlinks

The following explains how to disable symlinks created when you install Puppet Enterprise.

You can disable symlinks by placing a setting in your your [default Hiera file](./config_intro.html#configure-settings-with-hiera).

1. In your default Hiera file, add the following setting:

   ~~~
   puppet_enterprise::manage_symlinks: false
   ~~~

***