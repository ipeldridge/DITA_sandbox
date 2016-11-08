<!--Multi-tasks can be used to introduce a process where each child task is required, or to group a set of similar tasks.-->

## Configure `pe_repo` for use with load balancers

This task provides instructions for properly configuring `pe_repo` when you use a load balancer with compile masters.

When installing a new Puppet agent from a load balanced pool of compile masters, the agent configuration will point to whichever compile master handled the request, instead of the load balancer itself. You need to override this behavior to by configuring the `pe_repo` class to send agent installation requests to the load balancer.

After configuring `pe_repo`, you need to make an additional classification change so that any newly provisioned compile masters will point to the master of masters (MoM) instead of the load balancer.

To properly configure `pe-repo` for use with a load balancer, complete the following task in the order specified.

Before you begin:

- Specifics on how to configure a load balancer infrastructure falls outside the scope of this document, but examples of how to leverage haproxy for this purpose can be found [in the HA proxy module documentation](https://forge.puppet.com/puppetlabs/haproxy).
- It's assumed you've already installed PE and, in the case of using load balancers, several compile masters.


### Configure `pe_repo` to send agent install requests to the load balancer

In this task, you configure `pe_repo` so agent installation requests will be sent to the load balancer.

1. From the console, click __Nodes__ > __Classification__, and select the __PE Master__ group.
2. In the __PE Master__ group, click the __Classes__ tab, and find the __pe_repo__ class.
2. From the __Parameter__ drop-down list, select __master__.
3. In the __Value__ field, enter the address your load balancer resolves to (for example, `LOADBALANCER.EXAMPLE.COM`).
4. Click __Add parameter__ and then the __Commit change__ button.



***