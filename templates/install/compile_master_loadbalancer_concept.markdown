<!--Concepts provide context for task and reference topics. -->

## Considerations when using load balancers with compile masters

The following are things to consider when using load balancers with compile masters. Specifics on how to configure a load balancer infrastructure falls outside the scope of this document, but examples of how to leverage haproxy for this purpose can be found [in the HA proxy module documentation](https://forge.puppet.com/puppetlabs/haproxy).

- Using health checks

   Puppet’s REST API exposes a status endpoint that can be leveraged from a load balancer health check to ensure that unhealthy hosts do not receive agent requests from the load balancer.

   The Puppet master service will respond to unauthenticated HTTP GET requests issued to `/puppet/v3/status/:name?environment=:environment` where `:name` is set to any alphanumeric value, and :environment is set to the name of any Puppet environment present on the host. A response with an HTTP 200 status code will be returned if the service is healthy.

   If your load balancer doesn’t support HTTP health checks, a simpler alternative is to check that the host is listening for TCP connections on port 8140. This ensures that requests will not be forwarded to an unreachable instance of the Puppet master, but it does not guarantee that a host will be pulled out of rotation if it is deemed to be unhealthy, or if the service listening on port 8140 is not a service related to Puppet.

- Optimizing workload distribution

   Due to the diverse nature of the network communications between the Puppet agent and the Puppet master, we recommend that you implement a load balancing algorithm that will distribute traffic between compile masters based on the number of open connections. Load balancers often refer to this strategy as “balancing by least connections.”

* * *
