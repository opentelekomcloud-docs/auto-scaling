:original_name: en-us_topic_0110252697.html

.. _en-us_topic_0110252697:

Basic Concepts
==============

**AS Group**

An AS group consists of a collection of instances that apply to the same scenario. It is the basis for enabling or disabling AS policies and performing scaling actions.

**AS Configuration**

An AS configuration is an Elastic Cloud Server (ECS) instance template in an AS group, specifying specifications of the ECS to be added, including the ECS type, vCPU, memory, image, disk, and login mode.

**AS Policy**

An AS policy specifies a condition for triggering a scaling action.

AS supports the following policies:

Alarm: AS automatically increases or decreases the number of instances in an AS group or sets the number of instances to a specified value if Cloud Eye generates an alarm for a configured metric, such as CPU usage.

Periodic: AS increases or decreases the number of instances in an AS group or sets the number of instances to a specified value at a configured interval, such as one day, one week, or month.

Scheduled: AS automatically increases or decreases the number of instances in an AS group or sets the number of instances to a specified value at a specified time.

**Instance**

An instance is an ECS in an AS group.

**Scaling Action**

A scaling action adds or removes instances to or from an AS group so that the number of instances in the AS group is the same as the expected number for proper service running.

When the number of instances in an AS group is not the same as expected, a scaling action is triggered. Specifically, when the scaling condition is met or you manually change the expected number of instances, a scaling action is triggered.
