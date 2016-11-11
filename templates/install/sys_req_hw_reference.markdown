<!--References present facts that users might need to understand or use a product.-->

## Puppet Enterprise hardware requirements

We provide the following hardware requirements for Puppet Enterprise, but please note these requirements may vary depending on the size and complexity of your PE infrastructure.

### Monolithic installations

The following requirements are for monolithic installations.

To manage up to 10 nodes, we recommend the following minimum hardware. 

Node volume |Cores | RAM       | /opt/   | EC2
------------|------ |-----------|---------|------
 10 or fewer|     2  | 6 GB   | 20 GB  | m3.xlarge instance
 
To manage more nodes you will need to upgrade your hardware. The default configuration of PE is tested to support up to 4000 nodes. To manage this many nodes, we recommend the following minimum hardware.

Node volume | Cores | RAM       | /opt/   | /var/ | EC2
------------|------|-----------|---------|-------|------
 10 - 4000  |  16 +  | 32 + GB   | 100 GB  | 10 GB | m3.xlarge or c4.4xlarge 

### Monolithic plus compile masters installations

The following requirements are for monolithic installations that use compile masters.

If you are managing more than 4000 nodes, you can add load-balanced compile masters to your monolithic installation to increase the amount of agents you can manage. Each compile master increases capacity by approximately 1500 - 3000 nodes, until you exhaust the capacity of PuppetDB or the PE console, which run on the MoM. If you start to see performance issues around 8000 nodes, you can adjust your hardware or move to a larger base infrastructure.

>**Note:** When you expand your deployment to use compile masters, you must also start using load balancers. It is simpler to upgrade your hardware in your monolithic installation, if you can, than to add compile masters and load balancers.

To manage more than 4000 nodes, we recommend the following minimum hardware.

<table>
  <tr>
    <th>Node volume</th>
    <th>Node</th>
    <th>Cores </th>
    <th>RAM</th>
    <th>/opt/</th>
    <th>/var/</th>
    <th>EC2</th>
  </tr>
  <tr>
    <td rowspan="2">4000 - 20,000</td>
    <td>Monolithic node</td>
    <td>16</td>
    <td>32</td>
    <td>150</td>
    <td>10</td>
    <td>c4.4xlarge</td>
  </tr>
  <tr>
    <td>Each compile master (1500 - 3000 nodes)</td>
    <td>4</td>
    <td>16</td>
    <td>30</td>
    <td>2</td>
    <td>m3.xlarge</td>
  </tr>
</table>           

To take full advantage of progressively larger hardware, you’ll need to configure PE to make use of those resources. See our guide to [configuring and tuning your PE infrastructure](./config_intro.html) for more information.

>**Note**: If you need to go beyond 20,000 nodes contact Puppet support or your sales team before setting up a large environment installation.

### Large environment installations

The following requirements are for monolithic installations that use compile masters.

A large environment installation is a high-capacity PE infrastructure. It runs on a split installation with additional compile masters and ActiveMQ message brokering. This installation is suitable for managing over 20,000 nodes. With this installation type, you will be able to support more nodes by adding more resources to PuppetDB and increasing the number of compile masters you have.  

We recommend, at minimum, the following hardware.

<table>
  <tr>
    <th>Node volume</th>
    <th>Node</th>
    <th>Cores </th>
    <th>RAM</th>
    <th>/opt/</th>
    <th>/var/</th>
    <th>EC2</th>
  </tr>
  <tr>
    <td rowspan="6">over 20,000</td>
    <td>Puppet master</td>
    <td>4</td>
    <td>16</td>
    <td>10</td>
    <td>42</td>
    <td>m3.xlarge or m4.xlarge</td>
  </tr>
  <tr>
    <td>PE console</td>
    <td>4</td>
    <td>4</td>
    <td>30</td>
    <td>22</td>
    <td>m3.xlarge or m4.xlarge </td>
  </tr>
  <tr>
    <td>PuppetDB</td>
    <td>32</td>
    <td>48</td>
    <td>200</td>
    <td>70</td>
    <td>m3.2xlarge </td>
  </tr>
  <tr>
    <td>(3) Compile master</td>
    <td>4</td>
    <td>16</td>
    <td>30</td>
    <td>42</td>
    <td>m3.xlarge or m4.xlarge </td>
  </tr>
  <tr>
    <td>ActiveMQ hubs</td>
    <td>2</td>
    <td>4</td>
    <td>10</td>
    <td>18</td>
    <td>m3.large instance</td>
  </tr>
  <tr>
    <td>ActiveMQ Spoke</td>
    <td>2</td>
    <td>4</td>
    <td>10</td>
    <td>18</td>
    <td>m3.large </td>
  </tr>
</table>

* * *
