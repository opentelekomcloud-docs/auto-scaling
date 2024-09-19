:original_name: as_06_0412.html

.. _as_06_0412:

Batch Managing AS Policies
==========================

Function
--------

This interface is used to enable, disable, or delete AS policies in batches.

-  A batch operation can be performed on a maximum of 20 AS policies at a time.

URI
---

POST /autoscaling-api/v1/{project_id}/scaling_policies/action

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

.. table:: **Table 2** Request parameters

   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type             | Description                                                                                                                           |
   +===================+=================+==================+=======================================================================================================================================+
   | scaling_policy_id | Yes             | Array of strings | Specifies the AS policy ID.                                                                                                           |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | action            | Yes             | String           | Specifies an action to be performed on AS policies in batches. The options are as follows:                                            |
   |                   |                 |                  |                                                                                                                                       |
   |                   |                 |                  | -  **delete**: deletes AS policies.                                                                                                   |
   |                   |                 |                  | -  **resume**: enables AS policies.                                                                                                   |
   |                   |                 |                  | -  **pause**: disables AS policies.                                                                                                   |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | force_delete      | No              | String           | Specifies whether to forcibly delete an AS policy. If the value is set to **no**, in-progress AS policies cannot be deleted. Options: |
   |                   |                 |                  |                                                                                                                                       |
   |                   |                 |                  | -  **no** (default): indicates that the AS policy is not forcibly deleted.                                                            |
   |                   |                 |                  | -  **yes**: indicates that the AS policy is forcibly deleted.                                                                         |
   |                   |                 |                  |                                                                                                                                       |
   |                   |                 |                  | This parameter is available only when **action** is set to **delete**.                                                                |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | delete_alarm      | No              | String           | Specifies whether to delete the alarm rule used by the alarm policy. The value can be **yes** or **no** (default).                    |
   |                   |                 |                  |                                                                                                                                       |
   |                   |                 |                  | This parameter is available only when **action** is set to **delete**.                                                                |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

This example enables the AS policies with IDs **policy_id1** and **policy_id2** in a batch.

.. code-block:: text

   POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_policies/action

   {
       "action": "resume",
       "scaling_policy_id": [
           "policy_id1",
           "policy_id2"
       ]
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
