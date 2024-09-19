:original_name: as_06_0103.html

.. _as_06_0103:

Recording AS Resource Operations
================================

Scenarios
---------

AS can work together with Cloud Trace Service (CTS) to record resource operations. CTS can record operations performed on the management console, operations performed by calling APIs, and operations triggered within the cloud system.

If you have enabled CTS, when a call is made to the AS API, the operation will be reported to CTS which will then deliver the operation record to a specified OBS bucket for storage. With CTS, you can record AS operation logs for later query, audit, and backtracking.

Obtaining AS Information in CTS
-------------------------------

After you enable CTS, whenever an AS API is called, the operation is recorded in a log file. On the **Cloud Trace Service** console, you can view operation records for the last 7 days. For details, see :ref:`Querying Real-Time Traces <as_06_0108>`. To store operation records for a longer period, you can transfer them to Object Storage Service (OBS) buckets.

:ref:`Table 1 <as_06_0103__table11766471458>` lists the AS operations that can be recorded by CTS.

.. _as_06_0103__table11766471458:

.. table:: **Table 1** AS operations that can be recorded by CTS

   +-----------------------------------------------+-----------------------+---------------------------------+
   | Operation                                     | Resource Type         | Trace Name                      |
   +===============================================+=======================+=================================+
   | Creating an AS group                          | scaling_group         | createScalingGroup              |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Modifying an AS group                         | scaling_group         | modifyScalingGroup              |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Deleting an AS group                          | scaling_group         | deleteScalingGroup              |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Enabling an AS group                          | scaling_group         | enableScalingGroup              |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Disabling an AS group                         | scaling_group         | disableScalingGroup             |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Performing operations on an AS group          | scaling_group         | operateScalingGroup             |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Creating an AS configuration                  | scaling_configuration | createScalingConfiguration      |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Deleting an AS configuration                  | scaling_configuration | deleteScalingConfiguration      |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Deleting AS configurations in a batch         | scaling_configuration | batchDeleteScalingConfiguration |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Creating an AS policy                         | scaling_policy        | createScalingPolicy             |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Modifying an AS policy                        | scaling_policy        | modifyScalingPolicy             |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Deleting an AS policy                         | scaling_policy        | deleteScalingPolicy             |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Enabling an AS policy                         | scaling_policy        | enableScalingPolicy             |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Disabling an AS policy                        | scaling_policy        | disableScalingPolicy            |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Executing an AS policy                        | scaling_policy        | executeScalingPolicy            |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Performing operations on an AS policy         | scaling_policy        | operateScalingPolicy            |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Enabling AS policies in a batch               | scaling_policy        | batchEnableScalingPolicies      |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Disabling AS policies in a batch              | scaling_policy        | batchDisableScalingPolicies     |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Removing an instance                          | scaling_instance      | removeInstance                  |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Removing instances in batches                 | scaling_instance      | batchRemoveInstances            |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Adding instances in batches                   | scaling_instance      | batchAddInstances               |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Performing operations on instances in batches | scaling_instance      | batchOperateInstance            |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Enabling instance protection in a batch       | scaling_instance      | batchProtectInstances           |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Disabling instance protection in a batch      | scaling_instance      | batchUnprotectInstances         |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Putting instances into standby in a batch     | scaling_instance      | batchEnterStandbyInstances      |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Deleting a tag                                | scaling_tag           | deleteScalingTag                |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Adding a tag                                  | scaling_tag           | createScalingTag                |
   +-----------------------------------------------+-----------------------+---------------------------------+
   | Updating a tag                                | scaling_tag           | updateScalingTag                |
   +-----------------------------------------------+-----------------------+---------------------------------+
