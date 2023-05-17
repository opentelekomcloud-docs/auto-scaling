:original_name: as_06_0103.html

.. _as_06_0103:

Recording AS Resource Operations
================================

Scenarios
---------

AS can use the Cloud Trace Service (CTS) to record resource operations. CTS can record operations performed on the management console, operations performed by calling APIs, and operations triggered within the cloud system.

If you have enabled CTS, when a call is made to the AS API, the operation will be reported to CTS which will then deliver the operation record to a specified OBS bucket for storage. With CTS, you can record operations associated with AS for later query, audit, and backtrack operations.

Obtaining AS Information in CTS
-------------------------------

After you enable CTS in the application system, the system logs the API calling operations performed on AS resources. On the **Cloud Trace Service** console, you can view operation records for the last 7 days. To obtain more operation records, you can enable the Object Storage Service (OBS) and synchronize operation records to the OBS in real time.

:ref:`Table 1 <as_06_0103__table11766471458>` lists the AS operations that can be recorded by CTS.

.. _as_06_0103__table11766471458:

.. table:: **Table 1** AS operations that can be recorded by CTS

   +------------------------------------------+-----------------------+---------------------------------+
   | Operation                                | Resource Type         | Trace Name                      |
   +==========================================+=======================+=================================+
   | Creating an AS group                     | scaling_group         | createScalingGroup              |
   +------------------------------------------+-----------------------+---------------------------------+
   | Modifying an AS group                    | scaling_group         | modifyScalingGroup              |
   +------------------------------------------+-----------------------+---------------------------------+
   | Deleting an AS group                     | scaling_group         | deleteScalingGroup              |
   +------------------------------------------+-----------------------+---------------------------------+
   | Enabling an AS group                     | scaling_group         | enableScalingGroup              |
   +------------------------------------------+-----------------------+---------------------------------+
   | Disabling an AS group                    | scaling_group         | disableScalingGroup             |
   +------------------------------------------+-----------------------+---------------------------------+
   | Creating an AS configuration             | scaling_configuration | createScalingConfiguration      |
   +------------------------------------------+-----------------------+---------------------------------+
   | Deleting an AS configuration             | scaling_configuration | deleteScalingConfiguration      |
   +------------------------------------------+-----------------------+---------------------------------+
   | Deleting AS configurations in batches    | scaling_configuration | batchDeleteScalingConfiguration |
   +------------------------------------------+-----------------------+---------------------------------+
   | Creating an AS policy                    | scaling_policy        | createScalingPolicy             |
   +------------------------------------------+-----------------------+---------------------------------+
   | Modifying an AS policy                   | scaling_policy        | modifyScalingPolicy             |
   +------------------------------------------+-----------------------+---------------------------------+
   | Deleting an AS policy                    | scaling_policy        | deleteScalingPolicy             |
   +------------------------------------------+-----------------------+---------------------------------+
   | Enabling an AS policy                    | scaling_policy        | enableScalingPolicy             |
   +------------------------------------------+-----------------------+---------------------------------+
   | Disabling an AS policy                   | scaling_policy        | disableScalingPolicy            |
   +------------------------------------------+-----------------------+---------------------------------+
   | Executing an AS policy                   | scaling_policy        | executeScalingPolicy            |
   +------------------------------------------+-----------------------+---------------------------------+
   | Removing an instance                     | scaling_instance      | removeInstance                  |
   +------------------------------------------+-----------------------+---------------------------------+
   | Removing instances in batches            | scaling_instance      | batchRemoveInstances            |
   +------------------------------------------+-----------------------+---------------------------------+
   | Adding instances in batches              | scaling_instance      | batchAddInstances               |
   +------------------------------------------+-----------------------+---------------------------------+
   | Enabling instance protection in a batch  | scaling_instance      | batchProtectInstances           |
   +------------------------------------------+-----------------------+---------------------------------+
   | Disabling instance protection in a batch | scaling_instance      | batchUnprotectInstances         |
   +------------------------------------------+-----------------------+---------------------------------+
   | Deleting a tag                           | scaling_tag           | deleteScalingTag                |
   +------------------------------------------+-----------------------+---------------------------------+
   | Creating or Updating a tag               | scaling_tag           | updateScalingTag                |
   +------------------------------------------+-----------------------+---------------------------------+

Viewing Audit Logs
------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select a region and a project.
#. Click **Service List**. Choose **Management & Deployment** > **Cloud Trace Service**.
#. Click **Trace List** in the navigation pane on the left.
#. You can use filters to query traces. The following filters are available:

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**: Select a filter from the drop-down list.

      If you select **Resource ID** for **Search By**, specify a resource ID.

      If you select **Data** for **Trace Type**, you can only filter traces by tracker.

   -  **Operator**: Select one or more specific operators from the drop-down list.

   -  **Trace Status**: Select **All trace statuses**, **Normal**, **Warning**, or **Incident**.

   -  Time range: In the upper right corner, choose **Last 1 hour**, **Last 1 day**, or **Last 1 week**, or specify a custom time range.

#. Click |image2| to the left of the required trace to expand its details.
#. Locate the required trace and click **View Trace** in the **Operation** column. The trace details are displayed.

CTS Log Entries
---------------

Each log entry consists of a trace in JSON format. A log entry indicates an AS API request, including the requested operation, the operation date and time, operation parameters, and information about the user who sends the request. The user information is obtained from the Identity and Access Management (IAM) service.

The following example shows CTS log entries for the **CreateScalingPolicy** action:

.. code-block::

   {
   "time": "2016-12-15 15:27:40 GMT+08:00",
   "user": {
   "name": "xxxx",
   "id": "62ff83d2920e4d3d917e6fa5e31ddebe",
   "domain": {
   "name": "xxx",
   "id": "30274282b09749adbe7d9cabeebcbe8b"
   }
   },
   "request": {
   "scaling_policy_name": "as-policy-oonb",
   "scaling_policy_action": {
   "operation": "ADD",
   "instance_number": 1
   },
   "cool_down_time": "",
   "scheduled_policy": {
   "launch_time": "2016-12-16T07:27Z"
   },
   "scaling_policy_type": "SCHEDULED",
   "scaling_group_id": "ec4051a7-6fbd-42d2-840f-2ad8cdabee34"
   },
   "response": {
   "scaling_policy_id": "6a38d488-664b-437a-ade2-dc45f96f7f4c"
   },
   "code": 200,
   "service_type": "AS",
   "resource_type": "scaling_policy",
   "resource_name": "as-policy-oonb",
   "resource_id": "6a38d488-664b-437a-ade2-dc45f96f7f4c",
   "source_ip": "10.190.205.233",
   "trace_name": "createScalingPolicy",
   "trace_rating": "normal",
   "trace_type": "ConsoleAction",
   "api_version": "1.0",
   "record_time": "2016-12-15 15:27:40 GMT+08:00",
   "trace_id": "f627062b-c297-11e6-a606-eb2c0f48bec5"
   }

.. |image1| image:: /_static/images/en-us_image_0142360107.png
.. |image2| image:: /_static/images/en-us_image_0108911462.jpg
