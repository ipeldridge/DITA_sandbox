<!--References present facts that users might need to understand or use a product.-->

## pe.conf parameter reference

The following sections detail the parameters that are mandatory or optional in `pe.conf` when installing or upgrading.

A `pe.conf` file is a [HOCON](./config_hocon.html) formatted file that declares parameters and values needed to install and configure PE.

>**Tip:** The example `pe.conf` packaged in the installer directory contains the mandatory parameters needed for a monolithic or split installation. You can use that example file without needing to create your own.

>**Warning:** Do not use single quotes on parameter values. Valid Boolean values are `true` or `false` (case sensitive, no quotation marks). **Do not use Yes (y), No (n), 1, or 0**.

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
    <td><code>"&lt;YOUR PASSWORD&gt;"</code></td>
    <td>The password used to log into the PE console.</td> 
  </tr>
  <tr>
    <td><code>"puppet_enterprise::puppet_master_host":</code></td>
    <td><code>"&lt;CONSOLE NODE FQDN&gt;"</code></td>
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
    <td nowrap><code>"console_admin_password":</code> "<PASSWORD>"</td>
    <td><code>"&lt;YOUR PASSWORD&gt;"</code></td>
    <td>The password used to log into the PE console.</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::puppet_master_host": "<FQDN>"</code></td>
    <td>The FQDN of the node hosting the Puppet master. (In a split install, do not use the `"%{::trusted.certname}"` value for the Puppet master.)</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::console_host": "<FQDN>"</code></td>
    <td>The FQDN of the node hosting the PE console.</td>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_host": "<FQDN>"</code></td>
    <td>The FQDN of the node hosting PuppetDB.</td>
  </tr>  
 </table>

### Database configuration parameters

The following are default parameters and values supplied for the PE databases. You can customize them as needed for monolithic or split installations.

<table>
  <tr>
    <th>Parameter</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::activity_database_name": "pe-activity"</code></td>
    <td>The name for the activity database.</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::activity_database_user": "pe-activity"</code></td>
    <td>The name for the activity database user.</td> 
  </tr> 
  <tr>
    <td nowrap><code>"puppet_enterprise::classifier_database_name": "pe-classifier"</code></td>
    <td>The name for the classifier database.</td> 
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::classifier_database_user": "pe-classifier"</code></td>
    <td>The name for the classifier database user.</td> 
  </tr> 
  <tr>
    <td nowrap><code>"puppet_enterprise::orchestrator_database_name": "pe-orchestrator"</code></td>
    <td>The name for the orchestrator database.</td>
  </tr>
  <tr>
    <td nowrap><code>"puppet_enterprise::orchestrator_database_user": "pe-orchestrator"</code></td>
    <td>The name for the orchestrator database user.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_database_name": "pe-puppetdb"</code></td>
    <td>The name for the PuppetDB database.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::puppetdb_database_user": "pe-puppetdb"</code></td>
    <td>The name for the PuppetDB database user.</td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::rbac_database_name": "pe-rbac"</code></td>
    <td>The name for the RBAC database. </td>
   </tr>
   <tr>
    <td nowrap><code>"puppet_enterprise::rbac_database_user": "pe-rbac"</code></td>
    <td>The password for the RBAC database user.</td>
   </tr> 
</table>        

### External PostgreSQL parameters

The following parameters are required if you're installing an external postgreSQL. The password parameters can be added to standard installations if needed.  

<table>
  <tr>
    <th>Parameter</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td no wrap><code>"puppet_enterprise::database_host": "<FQDN>"</code></td>
    <td>The FQDN of the node hosting the database component.</td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::database_ssl": false</code></td>
    <td>Leave this value as is for external PostgreSQL.</td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::database_cert_auth": false</code></td>
    <td>Leave this value as is for external PostgreSQL. </td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::puppetdb_database_password": "<STRING>"</code></td>
    <td>The password for the PuppetDB database user. </td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::classifier_database_password": "<STRING>"</code></td>
    <td>The password for the classifier database user.</td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::activity_database_password": "<STRING>"</code></td>
    <td>The password for the activity database user. </td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::rbac_database_password": "<STRING>"</code></td>
    <td>The password for the RBAC database user. </td>
   </tr>
   <tr>
    <td no wrap><code>"puppet_enterprise::orchestrator_database_password": "<STRING>"</code></td>
    <td>The password for the orchestrator database user. </td>
   </tr>
</table>   
  
### Additional parameters for monolithic and split installations

You can add these additional parameters to `pe.conf` as needed. They are not required.

<table>
  <tr>
   <th>Parameter</th>
   <th>Description</th>  
   <tr>
    <td no wrap><code>"pe_install::puppet_master_dnsaltnames": ["<STRING>"]</code></td>
    <td>DNS altnames to be added to the SSL certificate generated for the Puppet master node. The default <code>["puppet"]</code> is used if none are specified. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::code_manager_auto_configure": <true or false></code></td>
     <td> Whether or not to automatically configure the code manager service.<td>
   </tr> 
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::r10k_remote": "<STRING>" </code></td>
     <td>The git URL to be passed to the <code>r10k.yaml</code> file (for example, <code>git@<YOUR.GIT.SERVER.COM>:puppet/control.git</code>). This can be any URL that is supported by r10k (and normally git). This answer is only needed if you want r10k configured when PE is installed.</td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::r10k_private_key": "<STRING>"</code></td>
     <td> The local filesystem path on the Puppet master where the SSH private key can be found and used by r10k (for example, <code>/etc/puppetlabs/puppetserver/ssh/id-control_repo.rsa</code>). This answer is only needed if you want r10k configured when PE is installed. This must be specified in conjunction with <code>puppet_enterprise::profile::master::r10k_remote</code>. </td>
   </tr> 
   <tr>
     <td nowrap><code>"puppet_enterprise::use_application_services": <true or false></code></td>
     <td>Whether or not to enable Puppet Application Orchestration. If you choose not to enable this during installation, you can enable it at a later time. **This parameter is deprecated and will be removed in a future version. Refer to [Disabling application management](./config_orchestration.html#disabling-application-orchestration) or add the <code>puppet_enterprise::profile::master::app_management</code> parameter to <code>pe.conf</code> at install time.** </td>
   </tr>
   <tr>
     <td nowrap><code>puppet_enterprise::profile::master::app_management": false</code></td>
     <td>Disable application management at install time. Application management is on by default. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::puppetdb_port": "[INTEGER]"</code></td>
     <td>The SSL port PuppetDB listens on. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::check_for_updates": <true or false></code></td>
     <td>Whether to check for updates whenever the pe-puppetserver service restarts. Updates checks are enabled by default. See [Disabling update checking](./config_puppetserver.html#disabling-update-checking) for more information. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::master::use_legacy_auth_conf": <true or false></code></td>
     <td>Whether to use a legacy auth.conf file. Refer to [Changes to `auth.conf` when upgrading](./upgrade_mono.html#changes-to-auth.conf-when-upgrading) for details. </td>
   </tr>
   </table>
     
### Parameters for configuring and tuning Puppet Enterprise

You can use these parameters to configure and tune PE as needed. For more details about these settings, refer to [Configuring and tuning your Puppet Enterprise infrastructure](./config_intro.html). 

<table>
 <tr>
   <th>Parameter</th>
   <th>Description</th>
 </tr>
 <tr>
     <td nowrap><code>"puppet_enterprise::profile::amq::broker::heap_mb": <INTEGER></code></td>
     <td>The Puppet Master runs an ActiveMQ server to route commands. By default, its process uses a Java heap size of 512 MB.</td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::java_args": {"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to the Puppet Server service.</p> <p> For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "4096m", "Xms": "4096m"}</code></p></td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::puppetdb::java_args": {"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to the PuppetDB service.</p><p>For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "512m", "Xms": "512m"}</code></p> </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::console::java_args": {"JSON HASH"}</code></td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to console services.</p><p>For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "512m", "Xms": "512m"}</code></p> </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::orchestrator::java_args": {"JSON HASH"}</code> </td>
     <td><p>The JVM (Java Virtual Machine) memory that is allocated to orchestrations services.</p><p>For example: <code>"puppet_enterprise::profile::master::java_args": {"Xmx": "256m", "Xms": "256m"}</code></p> </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::master::puppetserver::jruby_max_active_instances": <INTEGER></code> </td>
     <td>Controls the maximum number of JRuby instances to allow on the Puppet Server.</td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::puppetdb::command_processing_threads": <INTEGER></code></td>
     <td>Defines how many command processing threads PuppetDB uses to sort incoming data. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::master::puppetdb::report_processor_ensure": "<present or absent>"</code> </td>
     <td>Determines if Puppet master generates agent run reports every time Puppet runs and submits these to PuppetDB. This setting is <code>present</code> (enabled) by default. </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::profile::console::classifier_synchronization_period": <INTEGER></code></td>
     <td>Controls how long it takes the node classifier (NC) to retrieve classes from the Puppet master. By default this value is set to 600 seconds (10 minutes). </td>
   </tr>
   <tr>
     <td nowrap><code>"puppet_enterprise::master::puppetserver::jruby_max_requests_per_instance": <INTEGER></code></td>
     <td>Sets the maximum number of requests per instance of a JRuby interpreter before it is killed. </td>
   </tr> 
   <tr>
     <td nowrap><code>"puppet_enterprise::master::puppetserver::jruby_environment_class_cache_enabled":</code></td>
     <td>Specifies whether cached data is used when updating classes in the console. The setting is disabled (`false`) by default. </td>
   </tr>
  </table>   
          
      
  

  
  
  
  
  





























* * *
