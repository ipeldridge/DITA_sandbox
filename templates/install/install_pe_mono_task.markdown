<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Web-based installation: monolithic

The following instructions are for installing a monolithic installation of PE using the web-based interface. When you perform a monolithic installation of PE, the master, console, and PuppetDB components are all installed on the same machine. 

Before you begin:

- [Review the installation prerequisites and notes](link)

- [Download and verify the appropriate PE tarball](./install_basic.html#downloading-puppet-enterprise).

1. Unpack the PE installation tarball. Run `tar -xf <tarball>`. (Note that you need about 1 GB of space in `/tmp` to untar the installer.) 
2. From the installer directory, run the installer with `sudo ./puppet-enterprise-installer`. 
3. When prompted, choose the “Guided” installation option. 

   At this point, the PE installer starts a web server and provides a web address: `https://<install platform hostname>:3000`. Ensure that port 3000 is reachable. If necessary, you can close port 3000 when the installation is complete.
   
   >**Warning**: Leave your terminal connection open until the installation is complete; otherwise, the installation will fail.
 
4. Paste the provided web address into your browser, and when prompted, accept the security request.

   >**Note:** The web-based installation uses a default SSL certificate; you’ll have to add a security exception in order to access the installer. This is safe to do.

5. On the start page, click **Let's get started**.
6. Choose whether to **Install on this server** or **Install on another server**.
7. Provide the following information about the Puppet master server:

   > **Note:** If you selected **Install on this server**, you will only be prompted for steps a and b.

   a. **Puppet master FQDN**: Provide the fully qualified domain name of the server you're installing PE on. This becomes the name of the Puppet master certificate. This FQDN must be resolvable from the machine on which you're running the installer.
   
      >**Tip:** To ensure you're using the proper FQDN for the monolithic Puppet master, run `sudo /opt/puppetlabs/bin/puppet config print certname` when the installation completes. If the installation fails because the FQDN value is incorrect, run the `config print certname` command and re-run the installer with the correct value.

   b. **DNS aliases**: Provide a comma-separated list of static, valid DNS names (default is "puppet"), so agents can trust the master if they contact it. You should make sure that this static list contains the DNS name or alias you’ll be configuring your agents to contact.

   c. **SSH username**: Provide the username to use when connecting to the Puppet master. This field defaults to `root`. This user must either be root or have sudo access.

   d. **SSH password**: If used, provide the password for the SSH username provided. This password will also be used if the user requires a password for sudo access.

   e. **SSH key file path**: If SSH password is not used, provide the absolute path to the SSH key on the machine you are performing the installation from. Defaults to the root SSH key path.

   f. **SSH key passphrase**: Provide if your SSH key is protected with a passphrase.

8. Provide the following information about database support (PuppetDB and PostgreSQL):

   a. **Install PostgreSQL on the PuppetDB host for me**: (Default) PE will install a PostgreSQL instance for the databases. This will use PE-generated default names and usernames for the databases. The passwords can be retrieved from `/etc/puppetlabs/installer/database_info.install` when the installation is complete.

   b. **Use an Existing PostgreSQL instance**: If you already have a PostgreSQL instance you'd like to use, you'll need to provide the following database information. Refer to [External PostgreSQL option and prep notes](./sys_req_extsql.html) for additional instructions about setting up your databases.

   - The PostgreSQL server DNS name

   - The port number used by the PostgreSQL server (default is 5432)

   - The PuppetDB database name (default is "pe-puppetdb")

   - The PuppetDB database user (default is "pe-puppetdb).

   - The PuppetDB database password

   - The role-based access control database name (default is "pe-rbac")

   - The role-based access control database user (default is "pe-rbac")

   - The role-based access control database password

   - The node classifier database name (default is "pe-classifier")

   - The node classifier database user (default is "pe-classifier")

   - The node classifier database password

   - The activity database name (default is "pe-activity")

   - The activity database user (default is "pe-activity")

   - The activity database password
   
   - The orchestrator database name (default is "pe-orchestrator")
   
   - The orchestrator database user (default is "pe-orchestrator")
   
   - The orchestrator database password
   
     > **Important**: After installing PE, refer to the [SSL for PE and PostgreSQL documentation](./install_ssl_postgresql.html) to enable SSL between PE and your external PostgreSQL instance.

7. Provide the following information about the PE console admin user:

   **Console superuser password**: Create a password for the console login. The password must be at least eight characters.

   >**Note**: The user name for the console admin user is __admin__.

8. Click **Submit**.

9. On the confirm plan page, review the information you provided, and, if it looks correct, click **Continue**.

    If you need to make any changes, click **Go Back** and make whatever changes you need.

10. On the validation page, the installer verifies various configuration elements. If there aren't any outstanding issues, click **Deploy now**.

    At this point, the PE installation starts. You can monitor the installation as it runs by toggling **Log View** and **Summary View**. If you notice any errors during the installation, check `/var/log/puppetlabs/installer/install_log.lastrun.<hostname>.log` on the machine from which you are running the installer.
   
    When the installation completes, the installer script that was running in the terminal will close. 
    
11. You can click **Start using Puppet Enterprise** to [log into the console](./console_accessing.html). 

>**Tip:** If you purchase Puppet Enterprise, you are sent a `license.key` file that lists how many nodes you can deploy. Refer to [Install the PE license key](link) for instructions on installing that key. 

* * *
