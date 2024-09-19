:original_name: en-us_topic_0042018372.html

.. _en-us_topic_0042018372:

Basic Concepts
==============

AS Group
--------

An AS group consists of a collection of ECS instances that apply to the same scenario. It is the basis for enabling or disabling AS policies and performing scaling actions.

AS Configuration
----------------

An AS configuration is a template specifying specifications for the ECS instances to be added to an AS group. The specifications include the ECS type, vCPUs, memory, image, and disk.

AS Policy
---------

AS policies can trigger scaling actions to adjust the number of instances in an AS group. An AS policy defines the condition to trigger a scaling action and the operation to be performed in a scaling action. When the triggering condition is met, the system automatically triggers a scaling action.

Scaling Action
--------------

A scaling action adds instances to or removes instances from an AS group. It ensures that the expected number of instances are running in the AS group by adding or removing instances when the triggering condition is met, which improves system stability.

Cooldown Period
---------------

To prevent an alarm-based policy from being repeatedly triggered by the same event, you can set a cooldown period. A cooldown period (in seconds) is the period of time between two scaling actions. AS recounts the cooldown period after a scaling action is complete. During the cooldown period, AS denies all scaling requests triggered by alarm-based policies. Scaling requests triggered manually or by scheduled or periodic policies are not affected.

For example, suppose that the cooldown period is set to 300 seconds (5 minutes), and a scheduled policy is specified to trigger a scaling action at 10:32, and a previous scaling action triggered by an alarm policy ends at 10:30. Any alarm-triggered scaling action will then be denied during the cooldown period from 10:30 to 10:35, but the scaling action scheduled for 10:32 will still take place. If the scheduled scaling action ends at 10:36, a new cooldown period starts at 10:36 and ends at 10:41.

Bandwidth Scaling
-----------------

AS automatically adjusts a bandwidth based on the scaling policies you configured.

After you configure a scaling policy as needed, when the trigger condition is met, AS automatically increases, decreases, or sets the bandwidth to a specified value based on the policy you configured. Three types of bandwidth scaling policies are available, including the alarm, scheduled, and periodic policy.

.. _en-us_topic_0042018372__en-us_topic_0190954061_section209534610470:

Region
------

A region is a geographic area where resources used by AS are located.

AZs in the same region can communicate with each other over an intranet, but AZs in different regions cannot.

Cloud data centers are deployed in locations around the world. You can use AS in different regions. Deploying AS in different regions allows you to tailor policies to better suit your requirements. For example, applications can be designed to meet user requirements in specific regions or comply with local laws or regulations.

Project
-------

A project is used to group and isolate resources, including compute, storage, and network resources. A project can be a department or a project team. Multiple projects can be created under one account.
