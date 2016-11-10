<!--Concepts provide context for task and reference topics. -->

## About Puppet Enterprise binaries and symlinks

PE installs a number of binaries and symlinks for interacting with its tools and services.

PE installs its binaries in `/opt/puppetlabs/bin`. To make essential Puppet tools available to all users, the installer automatically creates symlinks in `/usr/local/bin` for the `facter`, `puppet`, `pe-man`, `r10k`, `hiera`,  and `mco` binaries. Note that the symlinks will only be created if `/usr/local/bin` is writeable.

Note that AIX and Solaris 10/11 users need to add `/usr/local/bin` to their default path.

If you're running Mac OS X agents, note that symlinks are not created until the first successful Puppet run that applies the agents' catalogs.

Binaries provided by other PE components, such as those for interacting with PE's installed PostgreSQL server, PuppetDB, or Ruby packages do not have symlinks created. To include these binaries in your default `$PATH`, manually add them to your profile or run `PATH=/opt/puppetlabs/puppet/bin:/opt/puppetlabs/server/bin:$PATH;export PATH`.


* * *
