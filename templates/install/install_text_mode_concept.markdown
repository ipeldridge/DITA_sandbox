<!--Concepts provide context for task and reference topics. -->

## How text-mode installation works

When you run the Puppet Enterprise installer in text mode, you pass a configuration file (`pe.conf`), which contains values for the parameters needed to install PE, to the installer.

Text-mode installation requires you to run the installer with a `pe.conf` file on each node on which you are installing a PE component. In other words, for a monolithic installation, you run the installer with `pe.conf` on one node, but for a split installation, you run the installer with `pe.conf` on three nodes.

* [Monolithic text-mode installation instructions](./install_text_mode_mono.html)
* [Split text-mode installation instructions](./install_text_mode_split.html)

A `pe.conf` file is a [HOCON](./config_hocon.html) formatted file that declares parameters and values needed to install and configure PE. For example, you only need two key / value pairs for a monolithic installation:

~~~
"console_admin_password": "puppet"
"puppet_enterprise::puppet_master_host": "%{::trusted.certname}"
~~~

For a complete list of mandatory and optional parameters, see the [`pe.conf` parameter reference](./install_pe_conf_param.html).

You have a few options for creating or obtaining a `pe.conf` file to use during installations.

* Use the example `pe.conf` file provided in the `conf.d` directory in the PE installer tarball.

   >**Tip:** In most cases, for a monolithic installation, you can use the example `pe.conf` file without making any changes.

* When prompted by the installer, select the text-mode installation option. This opens your default editor with the example `pe.conf` file, which you can edit. Installation will proceed using that `pe.conf` after you quit the editor.
* Use the web-based installer to create a `pe.conf` file. After you run the web-based installer, you can find the file at `/etc/puppetlabs/enterprise/conf.d`. You can also download the file by following the link provided on the confirmation page of the web-based installer.

For a complete list of mandatory and optional parameters, see the [`pe.conf` parameter reference](./install_pe_conf_param.html).

* * *
