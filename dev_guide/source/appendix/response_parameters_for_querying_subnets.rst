:original_name: en-us_topic_0110252687.html

.. _en-us_topic_0110252687:

Response Parameters for Querying Subnets
========================================

**Response parameters are as follows.**

Parameter description

.. table:: **Table 1** Response parameter

   +-----------+------------------------------------------------------------------------------+------------------------------------------------------------------------------------+
   | Parameter | Type                                                                         | Description                                                                        |
   +===========+==============================================================================+====================================================================================+
   | subnets   | Array of :ref:`subnets <en-us_topic_0110252687__table1079195210520>` objects | Specifies the :ref:`subnets objects <en-us_topic_0110252687__table1079195210520>`. |
   +-----------+------------------------------------------------------------------------------+------------------------------------------------------------------------------------+

Descriptions of **subnets** fields

.. _en-us_topic_0110252687__table1079195210520:

.. table:: **Table 2** **subnets** objects

   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                              | Description                                                                                                                             |
   +=======================+===================================================================================+=========================================================================================================================================+
   | id                    | String                                                                            | Specifies a resource ID in UUID format.                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                            | -  Specifies the subnet name.                                                                                                           |
   |                       |                                                                                   | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                  |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                            | -  Provides supplementary information about the subnet.                                                                                 |
   |                       |                                                                                   | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                        |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                                            | Specifies the subnet CIDR block.                                                                                                        |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | gateway_ip            | String                                                                            | Specifies the subnet gateway address.                                                                                                   |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | dhcp_enable           | Boolean                                                                           | Specifies whether the DHCP function is enabled for the subnet.                                                                          |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | primary_dns           | String                                                                            | Specifies the IP address of DNS server 1 on the subnet.                                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | secondary_dns         | String                                                                            | Specifies the IP address of DNS server 2 on the subnet.                                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | dnsList               | Array of strings                                                                  | Specifies the IP address list of DNS servers on the subnet.                                                                             |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone     | String                                                                            | Identifies the AZ to which the subnet belongs.                                                                                          |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                                                                            | Specifies the ID of the VPC to which the subnet belongs.                                                                                |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                            | -  Specifies the status of the subnet.                                                                                                  |
   |                       |                                                                                   | -  The value can be **ACTIVE**, **UNKNOWN**, or **ERROR**.                                                                              |
   |                       |                                                                                   |                                                                                                                                         |
   |                       |                                                                                   |    -  **ACTIVE**: indicates that the subnet has been associated with a VPC.                                                             |
   |                       |                                                                                   |    -  **UNKNOWN**: indicates that the subnet has not been associated with a VPC.                                                        |
   |                       |                                                                                   |    -  **ERROR**: indicates that the subnet is abnormal.                                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | neutron_network_id    | String                                                                            | Specifies the ID of the corresponding network (OpenStack Neutron API).                                                                  |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | neutron_subnet_id     | String                                                                            | Specifies the ID of the corresponding subnet (OpenStack Neutron API).                                                                   |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | extra_dhcp_opts       | Array of :ref:`extra_dhcp_opt <en-us_topic_0110252687__table17713214828>` objects | Specifies the NTP server address configured for the subnet. For details, see :ref:`Table 3 <en-us_topic_0110252687__table17713214828>`. |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0110252687__table17713214828:

.. table:: **Table 3** **extra_dhcp_opt** object

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | opt_value       | No              | String          | -  Specifies the NTP server address or DHCP lease expiration time configured for the subnet.                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Constraints:                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |    The option **ntp** for **opt_name** indicates the NTP server configured for the subnet. Currently, only IPv4 addresses are supported. A maximum of four IP addresses can be configured, and each address must be unique. Multiple IP addresses must be separated using commas (,). The option **null** for **opt_name** indicates that no NTP server is configured for the subnet. The parameter value cannot be an empty string. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |    The option **addresstime** for **opt_name** indicates the DHCP lease expiration time. The value can be **-1**, which indicates unlimited lease time, or *Number*\ **+h**. The number ranges from 1 to 30,000. For example, the value can be **5h**. The default value is **24h**.                                                                                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | opt_name        | Yes             | String          | -  Specifies the NTP server address name or DHCP lease expiration time name configured for the subnet.                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                 | -  Currently, the value can only be set to **ntp** or **addresstime**.                                                                                                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Example response**

.. code-block::

   {
       "subnets": [
           {
               "id": "4779ab1c-7c1a-44b1-a02e-93dfc361b32d",
               "name": "subnet",
               "description": "",
               "cidr": "192.168.20.0/24",
               "dnsList": [
                   "114.xx.xx.114",
                   "114.xx.xx.115"
               ],
               "status": "ACTIVE",
               "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
               "gateway_ip": "192.168.20.1",
               "dhcp_enable": true,
               "primary_dns": "114.xx.xx.114",
               "secondary_dns": "114.xx.xx.115",
           "availability_zone": "aa-bb-cc",//For example, the AZ is aa-bb-cc.
               "neutron_network_id": "4779ab1c-7c1a-44b1-a02e-93dfc361b32d",
               "neutron_subnet_id": "213cb9d-3122-2ac1-1a29-91ffc1231a12",
               "extra_dhcp_opts": [
                 {
                   "opt_value": "10.100.0.33,10.100.0.34",
                   "opt_name": "ntp"
                 }
                 {
                   "opt_value": "24h",
                   "opt_name": "addresstime"
                 }
              ]
           },
           {
               "id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "name": "Subnet1",
               "description": "",
               "cidr": "192.168.1.0/24",
               "dnsList": [
                   "114.xx.xx.114",
                   "114.xx.xx.115"
               ],
               "status": "ACTIVE",
               "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
               "gateway_ip": "192.168.1.1",
               "dhcp_enable": true,
               "primary_dns": "114.xx.xx.114",
               "secondary_dns": "114.xx.xx.115",
           "availability_zone": "aa-bb-cc",//For example, the AZ is aa-bb-cc.
               "neutron_network_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "neutron_subnet_id": "1aac193-a2ad-f153-d122-12d64c2c1d78",
               "extra_dhcp_opts": [
                 {
                   "opt_value": "10.100.0.33,10.100.0.34",
                   "opt_name": "ntp"
                 },
                 {
                   "opt_value": "24h",
                   "opt_name": "addresstime"
                 }
              ],
           }
       ]
   }
