:original_name: en-us_topic_0110252688.html

.. _en-us_topic_0110252688:

Response Parameters for Querying Security Groups
================================================

**Response parameters are as follows.**

Parameter description

.. table:: **Table 1** Response parameter

   +-----------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                                | Description                                                                                                         |
   +=================+=====================================================================================+=====================================================================================================================+
   | security_groups | Array of :ref:`security_group <en-us_topic_0110252688__table1991161415017>` objects | Specifies the security group objects. For details, see :ref:`Table 2 <en-us_topic_0110252688__table1991161415017>`. |
   +-----------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0110252688__table1991161415017:

.. table:: **Table 2** Description of **security_group** fields

   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Mandatory       | Type            | Description                                                                                                                                                       |
   +=======================+=================+=================+===================================================================================================================================================================+
   | name                  | Yes             | String          | -  Specifies the security group name.                                                                                                                             |
   |                       |                 |                 | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                            |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | No              | String          | Specifies the resource ID of the VPC to which the security group belongs.                                                                                         |
   |                       |                 |                 |                                                                                                                                                                   |
   |                       |                 |                 | .. note::                                                                                                                                                         |
   |                       |                 |                 |                                                                                                                                                                   |
   |                       |                 |                 |    This parameter has been discarded, it is not recommended to use it.                                                                                            |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String          | -  Specifies the enterprise project ID. When creating a security group, associate the enterprise project ID with the security group.                              |
   |                       |                 |                 | -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. |
   |                       |                 |                 |                                                                                                                                                                   |
   |                       |                 |                 | .. note::                                                                                                                                                         |
   |                       |                 |                 |                                                                                                                                                                   |
   |                       |                 |                 |    This parameter is unsupported. Do not use it.                                                                                                                  |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **security_group_rules** objects

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================================================================================================================+
   | id                    | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | -  Provides supplementary information about the security group rule.                                                                                                                                                                                                |
   |                       |                       | -  The value is a string of no more than 255 characters that can contain letters and digits.                                                                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id     | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction             | String                | -  Specifies the direction of access control.                                                                                                                                                                                                                       |
   |                       |                       | -  The value can be **egress** or **ingress**.                                                                                                                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype             | String                | -  Specifies the IP protocol version.                                                                                                                                                                                                                               |
   |                       |                       | -  The value can be **IPv4** or **IPv6**.                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | String                | -  Specifies the protocol type.                                                                                                                                                                                                                                     |
   |                       |                       | -  The value can be **icmp**, **tcp**, **udp**, or others.                                                                                                                                                                                                          |
   |                       |                       | -  If the parameter is left blank, the security group supports all protocols.                                                                                                                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min        | int                   | -  Specifies the start port number.                                                                                                                                                                                                                                 |
   |                       |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                                |
   |                       |                       | -  The value cannot be greater than the **port_range_max** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <en-us_topic_0136596144>`.                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max        | int                   | -  Specifies the end port number.                                                                                                                                                                                                                                   |
   |                       |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                                |
   |                       |                       | -  If the protocol is not **icmp**, the value cannot be smaller than the **port_range_min** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <en-us_topic_0136596144>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix      | String                | -  Specifies the remote IP address. If the access control direction is set to **egress**, the parameter specifies the source IP address. If the access control direction is set to **ingress**, the parameter specifies the destination IP address.                 |
   |                       |                       | -  The value can be in the CIDR format or IP addresses.                                                                                                                                                                                                             |
   |                       |                       | -  The parameter is exclusive with parameter **remote_group_id**.                                                                                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id       | String                | -  Specifies the ID of the peer security group.                                                                                                                                                                                                                     |
   |                       |                       | -  The value is exclusive with parameter **remote_ip_prefix**.                                                                                                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Example response**

.. code-block::

   {
       "security_groups": [
           {
               "id": "16b6e77a-08fa-42c7-aa8b-106c048884e6",
               "name": "qq",
               "description": "qq",
               "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",

               "security_group_rules": [
                   {
                       "direction": "egress",
                       "ethertype": "IPv4",
                       "id": "369e6499-b2cb-4126-972a-97e589692c62",
                       "description": "",
                       "security_group_id": "16b6e77a-08fa-42c7-aa8b-106c048884e6"
                   },
                   {
                       "direction": "ingress",
                       "ethertype": "IPv4",
                       "id": "0222556c-6556-40ad-8aac-9fd5d3c06171",
                       "description": "",
                       "remote_group_id": "16b6e77a-08fa-42c7-aa8b-106c048884e6",
                       "security_group_id": "16b6e77a-08fa-42c7-aa8b-106c048884e6"
                   }
               ]
           },
           {
               "id": "9c0f56be-a9ac-438c-8c57-fce62de19419",
               "name": "default",
               "description": "qq",
               "vpc_id": "13551d6b-755d-4757-b956-536f674975c0",

               "security_group_rules": [
                   {
                       "direction": "egress",
                       "ethertype": "IPv4",
                       "id": "95479e0a-e312-4844-b53d-a5e4541b783f",
                       "description": "",
                       "security_group_id": "9c0f56be-a9ac-438c-8c57-fce62de19419"
                   },
                   {
                       "direction": "ingress",
                       "ethertype": "IPv4",
                       "id": "0c4a2336-b036-4fa2-bc3c-1a291ed4c431",
                       "description": "",
                       "remote_group_id": "9c0f56be-a9ac-438c-8c57-fce62de19419",
                       "security_group_id": "9c0f56be-a9ac-438c-8c57-fce62de19419"
                   }
               ]
           }
       ]
   }
