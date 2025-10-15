:original_name: en-us_topic_0110252696.html

.. _en-us_topic_0110252696:

Response Parameters for Querying Instances in an AS Group
=========================================================

**Response parameters are as follows.**

Parameter description

.. table:: **Table 1** Response parameters

   +-------------------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | Parameter               | Type                                                                                        | Description                                              |
   +=========================+=============================================================================================+==========================================================+
   | total_number            | Integer                                                                                     | Specifies the total number of resources.                 |
   +-------------------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | start_number            | Integer                                                                                     | Specifies the start line number.                         |
   +-------------------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | limit                   | Integer                                                                                     | Specifies the maximum number of resources to be queried. |
   +-------------------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | scaling_group_instances | Array of :ref:`scaling_group_instances <en-us_topic_0110252696__table101521663415>` objects | Specifies details about the instances in the AS group.   |
   +-------------------------+---------------------------------------------------------------------------------------------+----------------------------------------------------------+

**scaling_group_instances** field data structure description

.. _en-us_topic_0110252696__table101521663415:

.. table:: **Table 2** **scaling_group_instances** field description

   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                                           |
   +============================+=======================+=======================================================================================================+
   | instance_id                | String                | Specifies the instance ID.                                                                            |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | instance_name              | String                | Specifies the instance name.                                                                          |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_group_id           | String                | Specifies the ID of the AS group to which the instance belongs.                                       |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_group_name         | String                | Specifies the name of the AS group to which the instance belongs.                                     |
   |                            |                       |                                                                                                       |
   |                            |                       | Supports fuzzy search.                                                                                |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | life_cycle_state           | String                | Specifies the instance lifecycle status in the AS group.                                              |
   |                            |                       |                                                                                                       |
   |                            |                       | -  **INSERVICE**: The instance is enabled.                                                            |
   |                            |                       | -  **PENDING**: The instance is being added to the AS group.                                          |
   |                            |                       | -  **REMOVING**: The instance is being removed from the AS group.                                     |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | health_status              | String                | Specifies the instance health status.                                                                 |
   |                            |                       |                                                                                                       |
   |                            |                       | -  **INITIALIZING**: The instance is being initialized.                                               |
   |                            |                       | -  **NORMAL**: The instance is functional.                                                            |
   |                            |                       | -  **ERROR**: The instance is faulty.                                                                 |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_configuration_name | String                | Specifies the AS configuration name.                                                                  |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_configuration_id   | String                | Specifies the AS configuration ID.                                                                    |
   |                            |                       |                                                                                                       |
   |                            |                       | If the returned value is not empty, the instance is an ECS automatically created in a scaling action. |
   |                            |                       |                                                                                                       |
   |                            |                       | If the returned value is empty, the instance is an ECS manually added to the AS group.                |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | create_time                | String                | Specifies the time when the instance is added to the AS group. The time format complies with UTC.     |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | protect_from_scaling_down  | Boolean               | Specifies the instance protection status.                                                             |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

**Example response**

.. code-block::

   {
       "limit": 10,
       "total_number": 1,
       "start_number": 0,
       "scaling_group_instances": [
           {
               "instance_id": "b25c1589-c96c-465b-9fef-d06540d1945c",
               "scaling_group_id": "e5d27f5c-dd76-4a61-b4bc-a67c5686719a",
               "scaling_group_name": "discuz",
               "life_cycle_state": "INSERVICE",
               "health_status": "NORMAL",
               "scaling_configuration_name": "discuz",
               "scaling_configuration_id": "ca3dcd84-d197-4c4f-af2a-cf8ba39696ac",
               "create_time": "2015-07-23T06:47:33Z",
               "instance_name": "discuz_3D210808",
               "protect_from_scaling_down": false
           }
       ]
   }
