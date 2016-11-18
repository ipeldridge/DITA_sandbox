### (Optional) Install agents without `curl -k`

In the instructions for installing agents with PE package management, the `-k` flag is needed in order to get `curl` to trust the master, which it wouldn't otherwise since Puppet and its SSL infrastructure have not yet been set up on the node. 

If you choose not to use `curl -k`, you can transfer the Puppet master CA certificate to any machines you want to install agents on, and then run the installation script against that cert. 

1. On the machine that will become the agent node, create the following directory: `/etc/puppetlabs/puppet/ssl/certs`.
2. On the Puppet master, navigate to `/etc/puppetlabs/puppet/ssl/certs/` and transfer `ca.pem` to the directory you made on the agent node in the previous step.    
3. On the agent node, make sure the file permissions are correct.

   ~~~
   chmod 444 /etc/puppetlabs/puppet/ssl/certs/ca.pem
   ~~~
   
4. When following the agent install instructions, use the --cacert flag to point to the Puppet master CA.

   ~~~
   curl --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem https://<PUPPET MASTER HOSTNAME>:8140/packages/current/install.bash | sudo bash
   ~~~

See the [system requirements](./sys_req_os.html#aix) for more information about AIX, curl, and OpenSSL.

Users of AIX 5.3, 6.1, and 7.1 should note that the `-k` is not supported. You should replace the `-k` flag with `-tlsv1` or `-1`.

* * *
