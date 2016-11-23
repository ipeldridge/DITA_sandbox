<!--Multi-tasks can be used to introduce a process where each child task is required, or to group a set of similar tasks.-->

## Signing agent certificates

The following instructions explain how to sign Puppet agent certificates in the PE console or from the command line. 

After the first Puppet run, which the installer should trigger at the end of installation (or it can be triggered manually with `puppet agent -t`), the agent will automatically submit a certificate request to the Puppet master. Before the agent can fetch configurations or appear in the PE console, an administrator needs to sign its certificate request. This helps prevent unauthorized nodes from intercepting sensitive configuration data.

Pending node requests are indicated in the main navigation bar, and requests can be signed from the PE console or the command line.

### Signing agent certificates from the PE console

The following instructions explain how to sign agent certs from the PE console.

1. In the PE console, click **Nodes** > **Unsigned Certificates** to load a list of currently pending node requests.

2. Click the __Accept All__ button to approve the signing requests.

### Signing agent certificates from the command line

The following instructions explain how to sign agent certificates from the command line.

1. View the list of pending certificate requests. On the command line of the Puppet master, run the following command:

   ~~~
   sudo puppet cert list
   ~~~

2. To sign a request for an agent, run the following the command:

   ~~~
   sudo puppet cert sign <AGENT CERT NAME>
   ~~~
   
After signing a new node's certificate, it may take up to 30 minutes before that node appears in the console and begins retrieving configurations. You can use the CLI to trigger a Puppet run manually on the node if you want to see it right away

* * *




<!--console_cert_mgmt.html#rejecting-and-approving-nodes is probably a better topic to use-->