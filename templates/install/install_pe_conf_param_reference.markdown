<!--References present facts that users might need to understand or use a product.-->

## pe.conf parameter reference

The following sections detail the parameters that are mandatory or optional in `pe.conf` when installing or upgrading.

A `pe.conf` file is a [HOCON](./config_hocon.html) formatted file that declares parameters and values needed to install and configure PE. The following is a valid paramater and value expression:

~~~
"console_admin_password": "mypassword"
~~~

>**Tip:** The example `pe.conf` packaged in the installer directory contains the mandatory parameters needed for a monolithic or split installation. You can use that example file without needing to create your own.

>**Warning:** Do not use single quotes on parameter values. Use double quotes as shown in the examples.
>
> Valid Boolean values are `true` or `false` (case sensitive, no quotation marks). **Do not use Yes (y), No (n), 1, or 0**.

### Required parameters for monolithic installations

The following parameters are mandatory for a [monolithic installation](./install_text_mode_mono.html).

<table>
  <tr>
    <th>Parameter</th>
    <th> Value </th>
    <th>Definition</th>
  </tr>
  <tr>
    <td><code>"console_admin_password": </code></td>
    <td nowrap><code>"YOUR PASSWORD"</code></td>
    <td>The password used to log into the PE console.</td> 
  </tr>
  <tr>
    <td><code>"puppet_enterprise::puppet_master_host":</code></td>
    <td nowrap><code>"CONSOLE NODE FQDN"</code></td>
    <td>The FQDN of the node hosting the Puppet master. (You can leave this set to the <code>"%{::trusted.certname}"</code> value.)</td> 
  </tr>
 </table>

### Required parameters for split installations

The following parameters are mandatory for a [split installation](./install_text_mode_split.html).

<table>
  <tr>
    <th>Parameter</th>
    <th>Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td nowrap><code>"console_admin_password":</code></td>
    <td nowrap><code>"YOUR PASSWORD"</code></td>
    <td>The password used to log into the PE console.</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::puppet_master_host":</code></td>
    <td nowrap><code>"PUPPET MASTER NODE FQDN"</code></td>
    <td>The FQDN of the node hosting the Puppet master. (In a split install, do not use the <code>"%{::trusted.certname}"</code> value for the Puppet master.)</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::console_host":</code></td>
    <td nowrap><code>"PE CONSOLE NODE FQDN"</code></td>
    <td>The FQDN of the node hosting the PE console.</td>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_host":</code></td>
    <td nowrap><code>"PUPPETDB NODE FQDN"</code></td>
    <td>The FQDN of the node hosting PuppetDB.</td>
  </tr>  
 </table>

### Database configuration parameters

The following are default parameters and values supplied for the PE databases. You can customize them as needed for monolithic or split installations.

<table>
  <tr>
    <th>Parameter</th>
    <th>Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::activity_database_name":</code></td>
    <td nowrap><code>"pe-activity"</code> (default)</td>
    <td>The name for the activity database.</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::activity_database_user": </code></td>
    <td nowrap><code>"pe-activity"</code> (default)</td>
    <td>The name for the activity database user.</td> 
  </tr> 
  <tr>
    <td nowrap><code>"puppet_enterprise::classifier_database_name":</code></td>
    <td nowrap><code> "pe-classifier"</code> (default)</td>
    <td>The name for the classifier database.</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::classifier_database_user":</code></td>
    <td nowrap><code> "pe-classifier"</code> (default)</td>
    <td>The name for the classifier database user.</td> 
  </tr> 
  <tr>
    <td nowrap><code>"puppet_enterprise::orchestrator_database_name":</code></td>
    <td nowrap><code> "pe-orchestrator"</code> (default)</td>
    <td>The name for the orchestrator database.</td>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::orchestrator_database_user":</code></td>
    <td nowrap><code> "pe-orchestrator"</code> (default)</td>
    <td>The name for the orchestrator database user.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_database_name":</code></td>
    <td nowrap><code> "pe-puppetdb"</code>(default)</td>
    <td>The name for the PuppetDB database.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_database_user":</code></td>
    <td nowrap><code> "pe-puppetdb"</code>(default)</td>
    <td>The name for the PuppetDB database user.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::rbac_database_name": </code></td>
    <td nowrap><code> "pe-rbac"</code>(default)</td>
    <td>The name for the RBAC database. </td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::rbac_database_user": "pe-rbac"</code></td>
    <td nowrap><code> "pe-rbac"</code>(default)</td>
    <td>The password for the RBAC database user.</td>
   </tr> 
</table>        

### External PostgreSQL parameters

The following parameters are required if you're installing an external postgreSQL. The password parameters can be added to standard installations if needed.  

<table>
  <tr>
    <th>Parameter</th>
    <th>Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::database_host":</code></td>
    <td nowrap><code>"DATABASE NODE FQDN"</code></td>
    <td>The FQDN of the node hosting the database component.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::database_ssl":</code></td>
    <td>Boolean. Default is false.</td>
    <td>Leave this value as is for external PostgreSQL.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::database_cert_auth":</code></td>
    <td>Boolean. Default is false.</td>
    <td>Leave this value as is for external PostgreSQL. </td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_database_password":</code></td>
    <td nowrap><code>"PASSWORD" </code>(Must be a string.)</td>
    <td>The password for the PuppetDB database user. </td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::classifier_database_password":</code></td>
    <td nowrap><code>"PASSWORD" </code>(Must be a string.)</td>
    <td>The password for the classifier database user.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::activity_database_password":</code></td>
    <td nowrap><code>"PASSWORD" </code>(Must be a string.)</td>
    <td>The password for the activity database user. </td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::rbac_database_password":</code></td>
    <td nowrap><code>"PASSWORD" </code>(Must be a string.)</td>
    <td>The password for the RBAC database user. </td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::orchestrator_database_password":</code></td>
    <td nowrap><code>"PASSWORD" </code>(Must be a string.)</td>
    <td>The password for the orchestrator database user. </td>
   </tr>
</table>   
  
### Additional parameters for monolithic and split installations

You can add these additional parameters to `pe.conf` as needed. They are not required.

<table>
  <tr>
   <th>Parameter</th>
   <th>Value</th>
   <th>Description</th>  
   </tr>
   <tr>
    <td no wrap><code>"pe_install::puppet_master_dnsaltnames":</code></td>
    <td nowrap><code>["DNS ALT NAMES"]</code> (Must be a string.)</td>
    <td>DNS altnames to be added to the SSL certificate generated for the Puppet master node. The default <code>["puppet"]</code> is used if none are specified. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::code_manager_auto_configure":</code></td>
     <td nowrap><code>Boolean </code></td>
     <td> Whether or not to automatically configure the code manager service.</td>
   </tr> 
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::r10k_remote":</code></td>
     <td nowrap><code>"GIT URL" </code>(Must be a string.)</td>
     <td>The git URL to be passed to the r10k.yaml file (for example, <code>git@&lt;YOUR.GIT.SERVER.COM&gt;:puppet/control.git </code>). This can be any URL that is supported by r10k (and normally git). This answer is only needed if you want r10k configured when PE is installed.</td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::r10k_private_key":</code></td>
     <td nowrap><code>"PRIVATE KEY" </code>(Must be a string.)</td>
     <td> The local filesystem path on the Puppet master where the SSH private key can be found and used by r10k (for example, <code>/etc/puppetlabs/puppetserver/ssh/id-control_repo.rsa</code>). This answer is only needed if you want r10k configured when PE is installed. This must be specified in conjunction with <code>puppet_enterprise::profile::master::r10k_remote</code>. </td>
   </tr> 
   <tr>
     <td nowrap><code>puppet_enterprise::profile::master::app_management": </code></td>
     <td nowrap>Boolean. Default is true.</td>
     <td>Disable application management at install time. Application management is on by default. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::puppetdb_port":</code></td>
     <td nowrap><code>"[PORT NUMBER]" </code>(Must be an integer.)</td>
     <td>The SSL port PuppetDB listens on. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::check_for_updates":</code></td>
     <td nowrap>Boolean. Default is true.</td>
     <td>Whether to check for updates whenever the pe-puppetserver service restarts. Updates checks are enabled by default. See [Disabling update checking](./config_puppetserver.html#disabling-update-checking) for more information. </td>
   </tr>
</table>
     
### Parameters for configuring and tuning Puppet Enterprise

You can use these parameters to configure and tune PE as needed. For more details about these settings, refer to [Configuring and tuning your Puppet Enterprise infrastructure](./config_intro.html). 

<table>
 <tr>
   <th>Parameter</th>
   <th>Value</th>
   <th>Description</th>
 </tr>
 <tr>
     <td nowrap><code>"puppet_enterprise::profile::amq::broker::heap_mb":</code></td>
     <td>Heap value. Must be an integer. </td>
     <td>The Puppet Master runs an ActiveMQ server to route commands. By default, its process uses a Java heap size of 512 MB.</td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::java_args":</code></td>
     <td nowrap><code>{"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to the Puppet Server service.</p> <p> For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "4096m", "Xms": "4096m"}</code></p></td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::puppetdb::java_args":</code></td>
     <td nowrap><code>{"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to the PuppetDB service.</p><p>For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "512m", "Xms": "512m"}</code></p> </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::console::java_args":</code></td>
     <td nowrap><code>{"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to console services.</p><p>For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "512m", "Xms": "512m"}</code></p> </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::orchestrator::java_args":</code> </td>
     <td nowrap><code>{"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to orchestrations services.</p><p>For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "256m", "Xms": "256m"}</code></p> </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::master::puppetserver::jruby_max_active_instances":</code> </td>
     <td>Max active instances. Must be an integer. </td>
     <td>Controls the maximum number of JRuby instances to allow on the Puppet Server.</td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::puppetdb::command_processing_threads":</code></td>
     <td>Number of command threads. Must be an integer. </td>
     <td>Defines how many command processing threads PuppetDB uses to sort incoming data. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::puppetdb::report_processor_ensure":</code> </td>
     <td>Must be "present" or "absent".</td>
     <td>Determines if Puppet master generates agent run reports every time Puppet runs and submits these to PuppetDB. This setting is <code>present</code> (enabled) by default. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::console::classifier_synchronization_period": </code></td>
     <td>Classifier synchronization period. Must be an integer. </td>
     <td>Controls how long it takes the node classifier (NC) to retrieve classes from the Puppet master. By default this value is set to 600 seconds (10 minutes). </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::master::puppetserver::jruby_max_requests_per_instance":</code></td>
     <td>Max requests per instance. Must be an integer. </td>
     <td>Sets the maximum number of requests per instance of a JRuby interpreter before it is killed. </td>
   </tr> 
   <tr>
     <td nowrap><code>"puppet_enterprise::master::puppetserver::jruby_environment_class_cache_enabled":</code></td>
     <td>Boolean. Default is false.</td>
     <td>Specifies whether cached data is used when updating classes in the console. The setting is disabled (`false`) by default. </td>
   </tr>
  </table>   
          
      
  

  
  
  
  
  





























* * *
