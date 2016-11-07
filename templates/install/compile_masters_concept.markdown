## How compile masters work

The following provides an overview of how compile masters work and relevant details about them.

As your infrastructure grows beyond 2000 managed nodes, a single Puppet master most likely won't be able to process all the requests and compile all the code for those Puppet agents. You can scale your infrastructure by adding compile masters to share the workload and provide quicker, more efficient compilation times. Compile masters perform many of the same functions as a Puppet master: they run file sync, contain a Puppet Server, and can host `pe_repo`. When you deploy compile masters, the main Puppet master is known as the master of masters (MoM).

> **Tip:** See the [PE hardware recommendations](./sys_req_hw.html) for guidance on base installation types and recommended hardware for each.

All compile masters contain a Puppet Server and a file sync client. If you use file sync, all the Puppet code in the code directory on your MoM is distributed to all compile masters. By default, compile masters check for code updates every five seconds.

The CA service is disabled on compile masters. A proxy service running on the compile master's Puppet Server directs CA requests to the MoM, which hosts the CA in default installations. Compile masters also have:

- `peadmin` (the MCollective client)
- `pe_repo` (PE's repo for agent installation)
- the controller profile (used in conjunction with PE client tools)

Compile master logs are kept at `/var/log/puppetlabs/puppetserver/`. 

> **Important:** Compile masters must run the [same OS major version, platform, and architecture](./sys_req_os.html#puppet-master-platforms) as the MoM.

