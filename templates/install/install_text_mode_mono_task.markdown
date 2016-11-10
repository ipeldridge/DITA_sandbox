<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Text-mode installation: monolithic

The following instructions are for performing a text-mode monolithic installation of PE. This installs the master, console, and PuppetDB components all on the same machine.

Before beginning:

- Review [the text mode installation overview](./install_text_mode.html)
- [Download and verify the appropriate PE tarball](./install_basic.html#downloading-puppet-enterprise).


2. Unpack the tarball by running `tar -xf <TARBALL_FILENAME>`. This requires about 1 GB of space in `/tmp`.
3. From the installer directory, run the installer. The installation steps will vary depending on the path you choose.

   * To have the installer open a copy of `pe.conf` for you to edit and install with, run the installer **without the `-c` flag**.

     ~~~
     sudo ./puppet-enterprise-installer
     ~~~
      
   * To use a `pe.conf` file that you've previously populated, run the installer **with the `-c` flag** pointed at the `pe.conf` file.

     ~~~
     sudo ./puppet-enterprise-installer -c <FULL PATH TO pe.conf>
     ~~~
     
     >**Warning:** If you're using a pre-populated file, be sure you've set the parameters correctly as detailed in the following steps.
  
4. If you ran the installer **without the -c flag**, select "text-mode" when prompted. 

   This opens your text editor with a `pe.conf` file that you can edit to match your infrastructure and add any additional text-mode installation options as needed. 

5. Set the following parameter:
   
   - `"console_admin_password": "<PASSWORD>"`— The password used to log into the PE console.
   
    >**Tip**: On a monolithic install, you can use the default value of `"%{::trusted.certname}"`if the certname of your monolithic server matches its FQDN.      
   
6. If you have an external PostgreSQL server, refer to the [external PostgreSQL parameters in the pe.conf reference](./install_pe_conf_param.html#external-postgresql-parameters) and add them to `pe.conf`.
   
7. Save and close the file.

   This starts the installation.

8. After the installation completes, run Puppet on the monolithic Puppet master by running `puppet agent -t`.

    When the installation completes, you can find an updated `pe.conf` file at `/etc/puppetlabs/enterprise/conf.d`.



* * *
