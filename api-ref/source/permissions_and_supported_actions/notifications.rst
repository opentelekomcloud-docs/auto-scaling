:original_name: as_07_0209.html

.. _as_07_0209:

Notifications
=============

+-------------------------------------------+---------------------------------------------------------------------------------------------+-------------------------+-------------+--------------------+
| Permission                                | API                                                                                         | Action                  | IAM Project | Enterprise Project |
+===========================================+=============================================================================================+=========================+=============+====================+
| Configuring notifications for an AS group | PUT /autoscaling-api/v1/{project_id}/scaling_notification/{scaling_group_id}                | as:notifications:set    | Y           | Y                  |
+-------------------------------------------+---------------------------------------------------------------------------------------------+-------------------------+-------------+--------------------+
| Querying notifications of an AS group     | GET /autoscaling-api/v1/{project_id}/scaling_notification/{scaling_group_id}                | as:notifications:list   | Y           | Y                  |
+-------------------------------------------+---------------------------------------------------------------------------------------------+-------------------------+-------------+--------------------+
| Deleting a notification of an AS group    | DELETE /autoscaling-api/v1/{project_id}/scaling_notification/{scaling_group_id}/{topic_urn} | as:notifications:delete | Y           | Y                  |
+-------------------------------------------+---------------------------------------------------------------------------------------------+-------------------------+-------------+--------------------+
