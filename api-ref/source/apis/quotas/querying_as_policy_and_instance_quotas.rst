:original_name: as_06_0702.html

.. _as_06_0702:

Querying AS Policy and Instance Quotas
======================================

Function
--------

This interface is used to query the total quotas and used quotas of AS policies and instances of a specified AS group by group ID.

URI
---

GET /autoscaling-api/v1/{project_id}/quotas/{scaling_group_id}

.. table:: **Table 1** Parameter description

   ================ ========= ====== ==========================
   Parameter        Mandatory Type   Description
   ================ ========= ====== ==========================
   project_id       Yes       String Specifies the project ID.
   scaling_group_id Yes       String Specifies the AS group ID.
   ================ ========= ====== ==========================

Request
-------

None

Example Request
---------------

This example queries the total quotas and used quotas of the AS policies and instances in the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/quotas/e5d27f5c-dd76-4a61-b4bc-a67c5686719a

Response
--------

.. table:: **Table 2** Response parameters

   +-----------+--------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Parameter | Type                                                   | Description                                                                                 |
   +===========+========================================================+=============================================================================================+
   | quotas    | :ref:`quotas <as_06_0702__table38082817101238>` object | Specifies quota details. For details, see :ref:`Table 3 <as_06_0702__table38082817101238>`. |
   +-----------+--------------------------------------------------------+---------------------------------------------------------------------------------------------+

.. _as_06_0702__table38082817101238:

.. table:: **Table 3** **quotas** field description

   +-----------+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | Parameter | Type                                                                | Description                                                                             |
   +===========+=====================================================================+=========================================================================================+
   | resources | Array of :ref:`resources <as_06_0702__table49912400111831>` objects | Specifies resources. For details, see :ref:`Table 4 <as_06_0702__table49912400111831>`. |
   +-----------+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------+

.. _as_06_0702__table49912400111831:

.. table:: **Table 4** **resources** field description

   +-----------------------+-----------------------+-----------------------------------------------+
   | Parameter             | Type                  | Description                                   |
   +=======================+=======================+===============================================+
   | type                  | String                | Specifies the quota type.                     |
   |                       |                       |                                               |
   |                       |                       | -  **scaling_Policy**: indicates AS policies. |
   |                       |                       | -  **scaling_Instance**: indicates instances. |
   +-----------------------+-----------------------+-----------------------------------------------+
   | used                  | Integer               | Specifies the used quota.                     |
   +-----------------------+-----------------------+-----------------------------------------------+
   | quota                 | Integer               | Specifies the total quota.                    |
   +-----------------------+-----------------------+-----------------------------------------------+
   | max                   | Integer               | Specifies the quota upper limit.              |
   +-----------------------+-----------------------+-----------------------------------------------+
   | min                   | Integer               | Specifies the quota lower limit.              |
   +-----------------------+-----------------------+-----------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "quotas": {
           "resources": [
               {
                   "type": "scaling_Policy",
                   "used": 2,
                   "quota": 50,
                   "max": 50,
                   "min": 0
               },
               {
                   "type": "scaling_Instance",
                   "used": 0,
                   "quota": 200,
                   "max": 1000,
                   "min": 0
               }
           ]
       }
   }

Returned Values
---------------

-  Normal

   200

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
