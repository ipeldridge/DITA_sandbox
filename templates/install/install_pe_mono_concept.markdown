<!--Concepts provide context for task and reference topics. -->

## Web-based installation prerequisites and notes

Review the following prerequisites and notes before performing a web-based installation of PE.

- If you've previously installed Puppet or PE, make sure that the machine you're installing PE on is totally free of any artifacts left over from the previous installation.

- Make sure that DNS is properly configured on the machines you're installing PE on. All nodes must **know their own hostnames.** This can be done by properly configuring reverse DNS on your local DNS server, or by setting the hostname explicitly. Setting the hostname usually involves the `hostname` command and one or more configuration files, while the exact method varies by platform. In addition, all nodes must be able to **reach each other by name.** This can be done with a local DNS server, or by editing the `/etc/hosts` file on each node to point to the proper IP addresses.

- You can run the installer from a machine that is part of your PE deployment or from a machine that is outside your deployment. If you want to run the installer from a machine that is part of your deployment, we recommend you run it from the same node assigned the console component (in a split install).

- The machine you run the installer from must have the same OS/architecture as your PE deployment.

- Please ensure that port 3000 is reachable, as the web-based installer uses this port. You can close this port when the installation is complete.

- The web-based installer does not support sudo configurations with `Defaults targetpw` or `Defaults rootpw`. Make sure your `/etc/sudoers` file does not contain, or else comment out, those lines.

- **For Debian Users**: If you gave the root account a password during the installation of Debian, sudo may not have been installed. In this case, you will need to either install PE as root, or install sudo on any node(s) on which you want to install PE.

- **A Note about Passwords**: In some cases, during the installation process, you'll be asked to supply passwords. The `'` (single quote) is forbidden in all passwords.

- **SSH Prerequisites and notes**

   > **Note**: If you plan on choosing **Install on this server** during the installation process, you do not need to take any additional steps to configure SSH.

   - If you have a properly configured SSH agent with agent forwarding enabled, you don't need to perform any additional SSH configurations. Your SSH agent will be used by the installer.

   - If you're using SSH keys to authenticate across the nodes of your PE installation, the public key for the user account performing the installation must be included in the `authorized_keys` file for that user account on each node that you're installing a PE component on, including the machine from which you're running the installer. This applies to root or non-root users.

   - The web-based installer will prompt for the user account name, the SSH private key location, and the SSH passphrase for each node on which you're installing a PE component.

   - Please review the following authentication options:

      - **Are you installing using root with a password?** The installer will ask you to provide the username and password for each node on which you're installing a PE component.
         * **Prerequisite**: Remote root SSH login must be enabled on each node, including the node from which you're running the installer.
   
      - **Are you installing using a non-root user with a password?** The installer will ask you to provide the username and password for each node on which you're installing a PE component.
         * **Prerequisite**: Sudo must be enabled for the non-root user on which you're installing a PE component.

      - **Are you installing using root with an SSH key?** The installer will ask you to provide the username, private key path, and key passphrase (as needed) for each node on which you're installing a PE component.
         * **Prerequisite**: Remote root SSH login must enabled on each node, including the node from which you're running the installer. And the public root ssh key must be added to `authorized_keys` on each node on which you're installing a PE component.

      - **Are you installing using a non-root user with an SSH key?** The installer will ask you to provide the username, private key path, and key passphrase (as needed) for each node on which you're installing a PE component.
        * **Prerequisite**: The non-root user SSH key must be added to `authorized_keys` on each node on which you're installing a PE component. And the non-root user must be granted sudo access on each box.



* * *
