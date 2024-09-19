:original_name: as_06_0105.html

.. _as_06_0105:

Deleting an AS Group
====================

Function
--------

This interface is used to delete a specified AS group.

-  **force_delete** specifies whether to forcibly delete an AS group, remove the ECS instances and release them when the AS group is running instances or performing scaling actions. By default, its value is **no**, which means not to forcibly delete the AS group.
-  If the value of **force_delete** is set to **no**, the AS group can be deleted only when both the following conditions are met:

   -  The AS group is performing no scaling action.
   -  The number of running ECS instances (**current_instance_number**) is **0**.

-  If the value of **force_delete** is set to **yes**, the AS group enters the **DELETING** state, rejecting new requests for scaling actions while completing the existing scaling actions. Then, all ECS instances are removed from the AS group and the AS group is deleted. Note that the manually added ECS instances will be removed from the AS group and the ECS instances automatically created by AS will be automatically deleted.

   .. caution::

      Forcibly deleting an AS group may not delete ECS instances in the group.

URI
---

DELETE /autoscaling-api/v1/{project_id}/scaling_group/{scaling_group_id}

.. table:: **Table 1** Parameter description

   +------------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                               |
   +==================+=================+=================+===========================================================================+
   | project_id       | Yes             | String          | Specifies the project ID.                                                 |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | scaling_group_id | Yes             | String          | Specifies the AS group ID.                                                |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------+
   | force_delete     | No              | String          | Specifies whether to forcibly delete an AS group. Options:                |
   |                  |                 |                 |                                                                           |
   |                  |                 |                 | -  **no** (default): indicates that the AS group is not forcibly deleted. |
   |                  |                 |                 | -  **yes**: indicates to forcibly delete an AS group.                     |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example deletes the AS group with ID **a8327883-6b07-4497-9c61-68d03ee193a1**.

.. code-block:: text

   DELETE https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group/a8327883-6b07-4497-9c61-68d03ee193a1?force_delete=yes

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
