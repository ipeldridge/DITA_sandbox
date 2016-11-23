<!--Tasks describe a procedure the user performs. Tasks typically include 7 or fewer steps. Consider breaking longer tasks into a multi-task process. Avoid shoehorning conceptual or reference information into tasks so that the task is more navigable and reusable.-->

## Clearing agent certificates

In some cases, you may need to remove an agent's certificates (for example, if you ever need to reinstall Puppet on a machine). The following instructions explain how to clear an agent's certificate. 

1. On the command line of the Puppet master, run the following command:

   ~~~
   puppet cert clean <AGENT CERT NAME>
   ~~~

* * *
