:original_name: as_06_1102.html

.. _as_06_1102:

Querying an API Version
=======================

Function
--------

This interface is used to query a specified API version of the AS service.

URI
---

GET /{api_version}

.. table:: **Table 1** Parameter description

   =========== ========= ====== =======================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== =======================================
   api_version Yes       String Specifies the ID of the AS API version.
   =========== ========= ====== =======================================

Request
-------

None

Example Request
---------------

This example queries the API version of V1.

.. code-block:: text

   GET https://{Endpoint}/v1

Response
--------

.. table:: **Table 2** Response parameters

   +-----------+-------------------------------------------------------+------------------------------------+
   | Parameter | Type                                                  | Description                        |
   +===========+=======================================================+====================================+
   | version   | :ref:`version <as_06_1102__table786171513527>` object | Specifies a specified API version. |
   +-----------+-------------------------------------------------------+------------------------------------+

.. _as_06_1102__table786171513527:

.. table:: **Table 3** **version** field description

   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                          | Description                                                                                             |
   +=======================+===============================================================================+=========================================================================================================+
   | id                    | String                                                                        | Specifies the API version ID.                                                                           |
   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | links                 | Array of :ref:`links <as_06_1102__t759e6d15d244474e8f286185ede143fb>` objects | Specifies the API URL. For details, see :ref:`Table 4 <as_06_1102__t759e6d15d244474e8f286185ede143fb>`. |
   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | min_version           | String                                                                        | Specifies the earliest supported API version number.                                                    |
   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | status                | String                                                                        | Specifies the API version status.                                                                       |
   |                       |                                                                               |                                                                                                         |
   |                       |                                                                               | -  **CURRENT**: indicates a primary version.                                                            |
   |                       |                                                                               | -  **SUPPORTED**: indicates an earlier version which is still supported.                                |
   |                       |                                                                               | -  **DEPRECATED**: indicates a deprecated version which may be deleted later.                           |
   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | updated               | String                                                                        | Specifies the release date of an API version.                                                           |
   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | version               | String                                                                        | Specifies the latest supported API version number.                                                      |
   +-----------------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _as_06_1102__t759e6d15d244474e8f286185ede143fb:

.. table:: **Table 4** **links** field description

   ========= ====== =================================================
   Parameter Type   Description
   ========= ====== =================================================
   href      String Specifies the API Uniform Resource Locator (URL).
   rel       String Specifies the API URL dependency.
   ========= ====== =================================================

Example Response
----------------

.. code-block::

   {
     "version": {
       "id": "v1",
       "links": [
         {
           "href": "https://as.XXX.mycloud.com/autoscaling-api/v1/",
           "rel": "self"
         }
       ],
       "min_version": "",
       "status": "CURRENT",
       "updated": "2016-06-30T00:00:00Z",
       "version": ""
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
