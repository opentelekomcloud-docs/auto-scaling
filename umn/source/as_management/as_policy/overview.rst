:original_name: en-us_topic_2019013003.html

.. _en-us_topic_2019013003:

Overview
========

AS policies can trigger scaling actions to adjust bandwidth or the number of instances in an AS group. An AS policy defines the conditions for triggering a scaling action and the operation to be performed in a scaling action. When the trigger condition is met, a scaling action is triggered automatically.

.. note::

   If multiple AS policies are applied to an AS group, a scaling action is triggered as long as any of the AS policies is invoked, provided that the AS policies do not conflict with each other.

   The number of instances in the AS group will never exceed the specified maximum and minimum numbers of instances.

Constraints
-----------

A maximum of 50 AS policies can be created for an AS group.

AS supports the following policies:
-----------------------------------

-  Alarm policy: AS automatically adjusts the number of instances in an AS group or sets the number of instances to the configured value when an alarm is generated for a configured metric, such as CPU Usage.
-  Scheduled policy: AS automatically increases or decreases the number of instances in an AS group or sets the number of instances to the configured value at a specified time.
-  Periodic policy: AS automatically increases or decreases the number of instances in an AS group or sets the number of instances to the configured value at a configured interval, such as daily, weekly, and monthly.

Resource Adjustment Modes
-------------------------

-  Dynamic

   AS adjusts the number of instances or bandwidth when an alarm policy is triggered.

   This mode is suitable for scenarios where workloads are unpredictable. Alarm policies are used to trigger scaling actions based on real-time monitoring data (such as CPU usage) to dynamically adjust the number of instances in the AS group.

-  Planned

   AS adjusts the number of instances or bandwidth when a periodic or scheduled policy is triggered.

   This mode is suitable for scenarios where workloads are periodic.

-  Manual

   You can change the size of an AS group manually. You can either add or remove instances to or from the AS group, or modify the expected number of instances of the AS group.
