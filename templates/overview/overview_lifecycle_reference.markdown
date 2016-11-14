<!--References present facts that users might need to understand or use a product.-->

## Puppet Enterprise support lifecycle

The Puppet Support Lifecycle policy provides guidelines for product support when Puppet Enterprise versions are released, and throughout the lifecycle of each version. This guide is to help customers strategically plan upgrades and version choices. 

Puppet Enterprise versions are in one of **three phases** of the Puppet Support Lifecycle. These phases are:

- **Mainstream support:** Puppet Enterprise versions in this phase receive security updates, bug fixes and the entitlement of technical support defined in the [support plan](https://puppet.com/content/puppet-enterprise-support-plans). Customers on current support plans can access all services from customer support, including the authenticated FAQ, the [customer support portal](https://support.puppet.com/hc/en-us/restricted?return_to=https%3A%2F%2Fsupport.puppet.com%2Fhc%2Fen-us) and other customer-facing sources (such as [ask.puppet.com](https://ask.puppet.com/questions/) and the [Puppet Forge](https://forge.puppet.com/)).

- **Limited support:** Puppet Enterprise versions in this phase are no longer eligible for security updates and bug fixes. Customers on valid support plans can access services from customer support, still receive SLA response times and utilize the other customer-facing resources listed above. Customers are always encouraged to upgrade to a fully-supported version of Puppet Enterprise. Puppet supports customers to upgrade to the current mainstream supported version(s) with a variety of assistance and resource options.

- **End-of-life (EOL):** Puppet Enterprise versions in this phase are no longer eligible for security updates, bug fixes, or anything other than "commercially reasonable" assistance from customer support. Customers in the process of upgrading to a fully-supported version may contact support. As with other support phases, customer-facing sources such as the community and the Puppet Forge are still available.

Puppet produces a **standard release** approximately every three months. That means customers will always have access to the latest feature and security updates. Some customers often prefer to retain the same base version for an extended period. Puppet releases a new **long term support (LTS)** release every 18 months. All **standard releases** receive **mainstream support** until the next standard release or LTS option is available. An LTS release receives mainstream support for 24 months after launch.

Puppet Enterprise makes use of open source tools and libraries in addition to commercial-only software. Projects which Puppet, Inc. owns and maintains, like Facter, the Puppet Agent and Server, and PuppetDB, are effectively "upstream" of the commercial releases, and as such will move faster and have shorter support lifecycles than Puppet Enterprise. We may discontinue updates to our open-source platform components before their commercial EOL dates. Puppet also bundles and distributes externally-maintained components, such as Ruby, Postgres, and the JVM. We vet upstream security and feature releases and will update supported versions according to customer demand and our [Product Security Policy](/security/vulnerability_submission_process.html).

Puppet provides either **mainstream** or **limited support** for the versions of Puppet Enterprise listed below. All versions older than Puppet Enterprise 3.8 are now End-of-life (EOL) and we encourage upgrading to the [latest version](https://puppet.com/download-puppet-enterprise).

PE versions     | Start mainstream support   | Start limited support      | EOL
----------------|--------------------------|--------------------------|---------
2016.4 (LTS) | October 20, 2016            | October 2018            | TBD
2016.2 | June 21, 2016            | October 20, 2016            | January 31, 2017
2016.1 | April 7, 2016            | June 21, 2016            | December 31, 2016
2015.3 | December 8, 2015           | April 7, 2016            | December 31, 2016
2015.2 | July 28, 2015            | December 8, 2015            | December 31, 2016
3.8 | April 28, 2015            | December 31, 2016            | December 31, 2016

See also the [operating system support lifecycle](https://docs.puppet.com/pe/latest/sys_req_os.html#operating-system-support-life-cycles). 








* * *
