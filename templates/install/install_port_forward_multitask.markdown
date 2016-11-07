<!--Multi-tasks can be used to introduce a process where each child task is required, or to group a set of similar tasks.-->

## Port forwarding to the PE installer

The web-based PE installer requires access to port 3000 on the machine you're running the installer from. If you cannot connect directly to port 3000, we suggest port forwarding (or "tunneling" to) the installer via SSH.

The method for enabling port forwarding depends on your platform.


### Port forwarding from a Linux machine

1. On the machine from which you're running the installer, run `ssh -L 3000:localhost:3000 jumphost.exmple.tld`.
      
2. Run the installer script as indicated in the [web-based installation instructions](link).
      
3. When prompted to enter the installer URL, instead navigate to `https://localhost:3000`.


### Port forwarding from a Windows machine 
      
1. Open PuTTY, and select **Sessions**.
       
2. In the **Host Name** field, enter the FQDN of the host you want to run the installer from.
       
3. Select **Tunnels**.
       
4. In the **Source Port** field, enter `3000`.
       
5. In the **Destination** field, enter `localhost:3000`.
       
6. Select **Local**.
       
7. Click **Add**, and then click **Open**.

8. When the installer asks you to launch the browser, use `https://localhost:3000`, and continue following the installation instructions. 
       

* * *
