<!--Concepts provide context for task and reference topics. -->

## Passing configuration parameters to the install script

When using PE package management to install agents, you can pass configuration settings to the agent install script.

On *nix-based systems, you can pass parameters to the end of the install script to specify configuration settings that will be added to `puppet.conf` and to specify settings for inclusion in `custom_attributes` and `extension_requests` sections of `csr_attributes.yaml`.

For example:

~~~
curl -k https://master.example.com:8140/packages/current/install.bash | sudo bash -s agent:certname=<certnameOtherThanFQDN> custom_attributes:challengePassword=<passwordForAutosignerScript> extension_requests:pp_role=<puppetNodeRole>
~~~

You can pass as many parameters as you need to. Follow the `section:key=value` pattern and leave one space between parameters.

Vist the [Configuration Reference]({{puppet}}/configuration.html) for a complete list of values for `puppet.conf`. Visit the [CSR attributes and certificate extensions]({{puppet}}/ssl_attributes_extensions.html) page for more information on settings for `csr_attributes.yaml`.

* * *
