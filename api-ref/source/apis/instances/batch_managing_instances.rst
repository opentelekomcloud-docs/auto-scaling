:original_name: as_06_0303.html

.. _as_06_0303:

Batch Managing Instances
========================

Function
--------

-  Add or remove instances to or from an AS group in batches.

   .. note::

      If the instances were manually added to an AS group, they are removed from the AS group but are not deleted.

-  Configure instance protection or cancel the configuration for the instances in an AS group in batches.

.. note::

   -  A batch operation can be performed on a maximum of 10 instances at a time. After instances are added to an AS group, the number of instances in the AS group cannot be greater than the maximum number of instances. After instances are removed from an AS group, the number of instances in the AS group cannot be less than the minimum number of instances.
   -  Instances can be added to an AS group only when the AS group is in the **INSERVICE** state and has no scaling action in progress.
   -  You can remove instances from an AS group only when no scaling action is in progress.
   -  To add instances to an AS group, ensure that the AZ of the instances falls within that of the AS group.
   -  Only instances in **INSERVICE** state can be removed from an AS group. Instance protection can be enabled or disabled only for **INSERVICE** instances.
   -  When the capacity of an AS group is automatically decreased, the instances with instance protection enabled will not be removed from the AS group.
   -  If the listener bound to the instance to be removed is the same as the listener in the AS group, the listener will be unbound from the instance. If the listener bound to the instance to be removed is different from the listener in the AS group, the binding relationship between the listener and instance will be reserved.

URI
---

POST /autoscaling-api/v1/{project_id}/scaling_group_instance/{scaling_group_id}/action

.. table:: **Table 1** Parameter description

   ================ ========= ====== ==========================
   Parameter        Mandatory Type   Description
   ================ ========= ====== ==========================
   project_id       Yes       String Specifies the project ID.
   scaling_group_id Yes       String Specifies the AS group ID.
   ================ ========= ====== ==========================

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                     |
   +=================+=================+==================+=================================================================================================================+
   | instances_id    | Yes             | Array of strings | Specifies the ECS ID.                                                                                           |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | instance_delete | No              | String           | Specifies whether to delete an instance when it is removed from an AS group.                                    |
   |                 |                 |                  |                                                                                                                 |
   |                 |                 |                  | Options:                                                                                                        |
   |                 |                 |                  |                                                                                                                 |
   |                 |                 |                  | -  **no** (default): The instance will not be deleted.                                                          |
   |                 |                 |                  |                                                                                                                 |
   |                 |                 |                  | -  **yes**: The instance will be deleted.                                                                       |
   |                 |                 |                  |                                                                                                                 |
   |                 |                 |                  |    If the instances were manually added to an AS group, they are removed from the AS group but are not deleted. |
   |                 |                 |                  |                                                                                                                 |
   |                 |                 |                  | This parameter takes effect only when the **action** is set to **REMOVE**.                                      |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | Specifies an action to be performed on instances in batches. The options are as follows:                        |
   |                 |                 |                  |                                                                                                                 |
   |                 |                 |                  | -  **ADD**: adds instances to the AS group.                                                                     |
   |                 |                 |                  | -  **REMOVE**: removes instances from the AS group.                                                             |
   |                 |                 |                  | -  **PROTECT**: enables instance protection.                                                                    |
   |                 |                 |                  | -  **UNPROTECT**: disables instance protection.                                                                 |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  This example adds two instances with IDs **instance_id_1** and **instance_id_2** to the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a** in a batch.

   .. code-block:: text

      POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_instance/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/action

      {
          "action": "ADD",
          "instances_id": [
              "instance_id_1",
              "instance_id_2"
          ]
      }

-  This example removes and deletes instances with IDs **instance_id_1** and **instance_id_2** from the AS group **e5d27f5c-dd76-4a61-b4bc-a67c5686719a** in a batch.

   .. code-block:: text

      POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_instance/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/action

      {
          "action": "REMOVE",
          "instances_id": [
              "instance_id_1",
              "instance_id_2"
          ],
          "instance_delete": "yes"
      }

Response
--------

None

Example Response
----------------

None

Returned Values
---------------

-  Normal

   204

-  Abnormal

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Returned Value                    | Description                                                                                |
   +===================================+============================================================================================+
   | 400 Bad Request                   | The server failed to process the request.                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | You must enter the username and password to access the requested page.                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | You are forbidden to access the requested page.                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The server could not find the requested page.                                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server could not be accepted by the client.                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must use the proxy server for authentication to process the request.                   |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request could not be processed due to a conflict.                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | Failed to complete the request because of an internal service error.                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the request is invalid.                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the system is unavailable.                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurred.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <as_07_0102>`.
