:original_name: as_06_0302.html

.. _as_06_0302:

Removing an Instance from an AS Group
=====================================

Function
--------

This interface is used to remove a specified instance from an AS group.

-  You can remove instances only in **INSERVICE** state and only when the number of instances after the removal is greater than or equal to the minimum number of instances allowed.

-  You can remove instances from an AS group only when no scaling action is in progress.

.. note::

   Manually added instances are removed from an AS group but are not deleted.

URI
---

DELETE /autoscaling-api/v1/{project_id}/scaling_group_instance/{instance_id}

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | Specifies the instance ID. For details, see :ref:`Querying Instances in an AS Group <as_06_0301>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | instance_delete | No              | String          | Specifies whether an instance is deleted when it is removed from the AS group.                     |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | Options:                                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | -  **no** (default): The instance will not be deleted.                                             |
   |                 |                 |                 | -  **yes**: The instance will be deleted.                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example removes the instance with ID **b25c1589-c96c-465b-9fef-d06540d1945c** from the AS group but does not delete the instance.

.. code-block:: text

   DELETE https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_instance/b25c1589-c96c-465b-9fef-d06540d1945c?instance_delete=no

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
