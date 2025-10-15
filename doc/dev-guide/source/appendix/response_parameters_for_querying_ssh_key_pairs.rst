:original_name: en-us_topic_0110252690.html

.. _en-us_topic_0110252690:

Response Parameters for Querying SSH Key Pairs
==============================================

**Response parameters are as follows.**

Parameter description

+-----------+---------------------+-----------------------------------------------------------------------------------------------------+
| Parameter | Type                | Description                                                                                         |
+===========+=====================+=====================================================================================================+
| keypairs  | List data structure | Specifies key pairs. For details, see :ref:`Table 1 <en-us_topic_0110252690__table16240210162214>`. |
+-----------+---------------------+-----------------------------------------------------------------------------------------------------+

.. _en-us_topic_0110252690__table16240210162214:

.. table:: **Table 1** **keypairs** field data structure description

   +-----------+---------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                      | Description                                                                                                        |
   +===========+===========================+====================================================================================================================+
   | keypair   | Dictionary data structure | Specifies details about a key pair. For details, see :ref:`Table 2 <en-us_topic_0110252690__table18363311162316>`. |
   +-----------+---------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0110252690__table18363311162316:

.. table:: **Table 2** **keypair** field description

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | fingerprint           | String                | Specifies fingerprint information about the key pair.      |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | name                  | String                | Specifies the key pair name.                               |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | type                  | String                | Specifies the key type, which is **ssh** by default.       |
   |                       |                       |                                                            |
   |                       |                       | This parameter is supported in microversion 2.2 and later. |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | public_key            | String                | Specifies information about the public key.                |
   +-----------------------+-----------------------+------------------------------------------------------------+

**Example response**

.. code-block::

   {
       "keypairs": [
           {
               "keypair": {
                   "fingerprint": "15:b0:f8:b3:f9:48:63:71:cf:7b:5b:38:6d:44:2d:4a",
                   "name": "keypair-601a2305-4f25-41ed-89c6-2a966fc8027a",
                   "type": "ssh",
                   "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQC+Eo/RZRngaGTkFs7I62ZjsIlO79KklKbMXi8F+KITD4bVQHHn+kV+4gRgkgCRbdoDqoGfpaDFs877DYX9n4z6FrAIZ4PES8TNKhatifpn9NdQYWA+IkU8CuvlEKGuFpKRi/k7JLos/gHi2hy7QUwgtRvcefvD/vgQZOVw/mGR9Q== Generated-by-Nova\n"
               }
           }
       ]
   }
