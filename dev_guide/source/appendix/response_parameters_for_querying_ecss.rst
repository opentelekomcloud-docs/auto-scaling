:original_name: en-us_topic_0110252691.html

.. _en-us_topic_0110252691:

Response Parameters for Querying ECSs
=====================================

**Response parameters are as follows.**

Parameter description

+---------------+---------------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Parameter     | Type                | Description                                                                                                                            |
+===============+=====================+========================================================================================================================================+
| servers       | List data structure | Specifies the ECSs to be queried. For details, see :ref:`Table 1 <en-us_topic_0110252691__table170818733211>`.                         |
+---------------+---------------------+----------------------------------------------------------------------------------------------------------------------------------------+
| servers_links | Array of objects    | Specifies the link of the next page in pagination query. For details, see :ref:`Table 2 <en-us_topic_0110252691__table1789102943213>`. |
+---------------+---------------------+----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0110252691__table170818733211:

.. table:: **Table 1** **servers** field data structure description

   +-----------+---------------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                | Description                                                                                                 |
   +===========+=====================+=============================================================================================================+
   | name      | String              | Specifies the ECS name.                                                                                     |
   +-----------+---------------------+-------------------------------------------------------------------------------------------------------------+
   | id        | String              | Specifies the unique identifier of the ECS.                                                                 |
   +-----------+---------------------+-------------------------------------------------------------------------------------------------------------+
   | links     | List data structure | Specifies ECS shortcut links. For details, see :ref:`Table 2 <en-us_topic_0110252691__table1789102943213>`. |
   +-----------+---------------------+-------------------------------------------------------------------------------------------------------------+

**links** field data structure description

.. _en-us_topic_0110252691__table1789102943213:

.. table:: **Table 2** **servers_links** and **links** field description

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   rel       String Specifies the shortcut link marker name.
   href      String Specifies the shortcut link.
   ========= ====== ========================================

**Example response**

.. code-block::

   {
       "servers": [
           {
               "id": "616fb98f-46ca-475e-917e-2563e5a8cd19",
               "links": [
                   {
                       "href": "http://openstack.example.com/v2/openstack/servers/616fb98f-46ca-475e-917e-2563e5a8cd19",
                       "rel": "self"
                   },
                   {
                       "href": "http://openstack.example.com/openstack/servers/616fb98f-46ca-475e-917e-2563e5a8cd19",
                       "rel": "bookmark"
                   }
               ],
               "name": "new-server-test"
           }
       ]
   }
