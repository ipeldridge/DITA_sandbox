<!--Concepts provide context for task and reference topics. -->

## How PE package management works

The Puppet master hosts a package repo used to install agents in your PE infrastructure.

The PE package management repo is created during installation of the Puppet master and serves packages over HTTPS using the same port as the Puppet master (8140). This means agents won't require any new ports to be open other than the one they already need to communicate with the Puppet master.

When you run the install script, it detects the OS on which it is running, sets up an apt, yum, or zipper repo that refers back to the Puppet master, and then pulls down and installs the `puppet-agent` packages. It also creates a basic `puppet.conf`, and kicks off a Puppet run.

Note that if the install script can't find agent packages corresponding to the agent's platform, it will fail with an error message telling you which `pe_repo` class you need to add to the master.


>**Warning**: Installing agents using the `pe_repo` class requires an internet connection. If you don't have access to the internet, refer to [installing agents in a Puppet Enterprise infrastructure without internet access](#installing-agents-in-a-puppet-enterprise-infrastructure-without-internet-access).

* * *
