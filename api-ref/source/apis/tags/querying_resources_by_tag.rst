:original_name: as_06_1004.html

.. _as_06_1004:

Querying Resources by Tag
=========================

Function
--------

This API is used to query resources in a project by tag.

By default, resources and resource tags are in descending order of their creation time.

URI
---

POST /autoscaling-api/v1/{project_id}/{resource_type}/resource_instances/action

.. table:: **Table 1** Parameter description

   +---------------+-----------+--------+-------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                             |
   +===============+===========+========+=========================================================================+
   | project_id    | Yes       | String | Specifies the project ID.                                               |
   +---------------+-----------+--------+-------------------------------------------------------------------------+
   | resource_type | Yes       | String | Specifies the resource type. An example value is **scaling_group_tag**. |
   +---------------+-----------+--------+-------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                             | Description                                                                                                                                                                                                             |
   +=================+=================+==================================================================+=========================================================================================================================================================================================================================+
   | tags            | No              | Array of :ref:`Tag <as_06_1004__table97581357153610>` objects    | Specifies filter criteria with tags included. A maximum of 10 keys can be contained. The structure body must be complete. For details, see :ref:`Table 3 <as_06_1004__table97581357153610>`.                            |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | No              | Array of :ref:`Tag <as_06_1004__table97581357153610>` objects    | Specifies filter criteria with any tag included. A maximum of 10 keys can be contained. For details, see :ref:`Table 3 <as_06_1004__table97581357153610>`.                                                              |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Array of :ref:`Tag <as_06_1004__table97581357153610>` objects    | Specifies filter criteria without tags included. A maximum of 10 keys can be contained. For details, see :ref:`Table 3 <as_06_1004__table97581357153610>`.                                                              |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | No              | Array of :ref:`Tag <as_06_1004__table97581357153610>` objects    | Specifies filter criteria without any tag included. A maximum of 10 keys can be contained. For details, see :ref:`Table 3 <as_06_1004__table97581357153610>`.                                                           |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String                                                           | Specifies the maximum number of query records. The maximum value is 1,000, and the minimum value is 1.                                                                                                                  |
   |                 |                 |                                                                  |                                                                                                                                                                                                                         |
   |                 |                 |                                                                  | -  If **action** is set to **count**, this parameter is invalid.                                                                                                                                                        |
   |                 |                 |                                                                  | -  If **action** is set to **filter**, the default value is **1000**.                                                                                                                                                   |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String                                                           | Marks the paging location (index position). You are advised to use the **offset** parameter to set the index position.                                                                                                  |
   |                 |                 |                                                                  |                                                                                                                                                                                                                         |
   |                 |                 |                                                                  | Marks the paging location (resource ID or index location).                                                                                                                                                              |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String                                                           | Specifies the operation, which can be **filter** or **count**.                                                                                                                                                          |
   |                 |                 |                                                                  |                                                                                                                                                                                                                         |
   |                 |                 |                                                                  | -  **filter**: indicates that resources are filtered by tag and the resources meeting the search criteria are returned on pages.                                                                                        |
   |                 |                 |                                                                  | -  **count**: indicates that resources are searched by tag and the number of resources meeting the search criteria is returned.                                                                                         |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String                                                           | Specifies the index position. The query starts from the next image indexed by this parameter. The value must be a non-negative number.                                                                                  |
   |                 |                 |                                                                  |                                                                                                                                                                                                                         |
   |                 |                 |                                                                  | You do not need to specify this parameter when querying resources on the first page. When you query resources on subsequent pages, set **offset** to the location returned in the response body for the previous query. |
   |                 |                 |                                                                  |                                                                                                                                                                                                                         |
   |                 |                 |                                                                  | -  If the **action** value is **count**, this parameter is invalid.                                                                                                                                                     |
   |                 |                 |                                                                  | -  If the **action** value is **filter**, the default value is **0**.                                                                                                                                                   |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of :ref:`match <as_06_1004__table197711657123614>` objects | Specifies fuzzy search. For details, see :ref:`Table 4 <as_06_1004__table197711657123614>`.                                                                                                                             |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | without_any_tag | Yes             | Boolean                                                          | If this parameter is set to **true**, all resources without tags are queried. In this case, the **tags**, **tags_any**, **not_tags**, and **not_tags_any** fields are ignored.                                          |
   +-----------------+-----------------+------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_1004__table97581357153610:

.. table:: **Table 3** **Tag** field description

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                                           |
   +=================+=================+==================+=======================================================================================================================================================================================================================================================================+
   | key             | Yes             | String           | Specifies the tag key. It contains a maximum of 36 Unicode characters. It cannot be left blank (This parameter is not verified in the search process.) A maximum of 10 keys are allowed and the key cannot be left blank or an empty string. Each key must be unique. |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values          | Yes             | Array of strings | Specifies tag values. A value contains a maximum of 43 Unicode characters. A key contains a maximum of 10 values. Each value of the same key must be unique.                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                                                                                                       |
   |                 |                 |                  | -  The asterisk (*) is reserved for the system. If the value starts with \*, it indicates that fuzzy match is performed for the digits following \*. The value cannot contain only asterisks (*).                                                                     |
   |                 |                 |                  | -  If the values are null (not default), it indicates **any_value** (querying any value). The resources contain one or multiple values listed in **values** will be found and displayed.                                                                              |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_1004__table197711657123614:

.. table:: **Table 4** **match** field description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================+
   | key             | Yes             | String          | Specifies the key based on which to query resources.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | The parameter value can only be **resource_name**.                                                                                                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Specifies the value. The value is a fixed dictionary value. A value contains a maximum of 255 Unicode characters. If the value is an empty string or **resource_id**, exact match is used. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  This example queries the details of AS groups of a tenant using the following search criteria: including the tag (key = **key1** and value = **value1**), excluding the tag (key = **key2** and value = **value2**), index position 100, and a maximum number of 100 records.

   .. code-block:: text

      POST https: //{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_tag/resource_instances/action

      {
          "offset": "100",
          "limit": "100",
          "action": "filter",
          "matches": [{
              "key": "resource_name",
              "value": "resource1"
          }],
          "not_tags": [{
              "key": "key2",
              "values": ["value2"]
          }],
          "tags": [{
              "key": "key1",
              "values": ["value1"]
          }]
      }

-  This example counts the number of AS groups for a tenant using the following search criteria: including the tag (key = **key1** and value = **value1**) and excluding the tag (key = **key2** and value = **value2**).

   .. code-block:: text

      POST https: //{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_tag/resource_instances/action

      {
          "action": "count",
          "not_tags": [{
              "key": "key2",
              "values": ["value2"]
          }],
          "tags": [{
              "key": "key1",
              "values": ["value1"]
          }],
          "matches": [{
              "key": "resource_name",
              "value": "resource1"
          }]
      }

Response
--------

.. table:: **Table 5** Response parameters

   +-------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type                                                                | Description                                                                                                                                                               |
   +=============+=====================================================================+===========================================================================================================================================================================+
   | resources   | Array of :ref:`Resource <as_06_1004__table111211234112010>` objects | Specifies tag resources. For details, see :ref:`Table 6 <as_06_1004__table111211234112010>`.                                                                              |
   +-------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | total_count | Integer                                                             | Specifies the total number of records. When **action** is set to **count**, only this parameter is returned. The values of **resources** and **marker** are not returned. |
   +-------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker      | String                                                              | Specifies the paging location identifier.                                                                                                                                 |
   +-------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_1004__table111211234112010:

.. table:: **Table 6** **Resource** field description

   +-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                   | Description                                                                                                                                                       |
   +=================+========================================================================+===================================================================================================================================================================+
   | resource_id     | String                                                                 | Specifies the resource ID.                                                                                                                                        |
   +-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_detail | String                                                                 | Specifies the resource details.                                                                                                                                   |
   +-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | Array of :ref:`ResourceTag <as_06_1004__table191301634112010>` objects | Specifies tags. If there is no tag, the field **tags** is taken as an empty array by default. For details, see :ref:`Table 7 <as_06_1004__table191301634112010>`. |
   +-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_name   | String                                                                 | Specifies the resource name. If there is no resource, this parameter is an empty string by default.                                                               |
   +-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_1004__table191301634112010:

.. table:: **Table 7** **ResourceTag** field description

   +-----------+--------+--------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                              |
   +===========+========+==========================================================================+
   | key       | String | Specifies the tag key. It contains a maximum of 36 Unicode characters.   |
   +-----------+--------+--------------------------------------------------------------------------+
   | value     | String | Specifies the tag value. It contains a maximum of 43 Unicode characters. |
   +-----------+--------+--------------------------------------------------------------------------+

Example Response
----------------

-  Example response when **action** is set to **filter**

   .. code-block::

      {
          "resources": [{
              "resource_id": "64af4b6f-ec51-4436-8004-7a8f30080c87",
              "resource_detail": "SCALING_GROUP_TAG",
              "tags": [{
                  "key": "key1","value": "value1"
              }],
              "resource_name": "as_scaling_group_1"
          },
          {
              "resource_id": "7122ef51-604b-40e7-b9b2-1de4cd78dc60",
              "resource_detail": "SCALING_GROUP_TAG",
              "tags": [{
                  "key": "key1","value": "value1"
              }],
              "resource_name": "as_scaling_group_2"
          }],
          "marker": "2",
          "total_count": 2
      }

-  Example response when **action** is set to **count**

   .. code-block::

      {
             "total_count": 1000
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
