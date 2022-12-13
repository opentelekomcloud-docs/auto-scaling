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

To prevent an alarm-based policy from being triggered repeatedly by the same event, configure a cooldown period. A cooldown period specifies how long any alarm-triggered scaling action will be disallowed after a previous scaling action is complete. This cooldown period does not apply to scheduled or periodic scaling actions.

For example, if you set the cooldown period to 300 seconds (5 minutes), and there is a scaling action scheduled for 10:32, but a previous scaling action was complete at 10:30, any alarm-triggered scaling actions will be denied during the cooldown period from 10:30 to 10:35, but the scheduled scaling action will still be triggered at 10:32. If the scheduled scaling action ends at 10:36, a new cooldown period starts at 10:36 and ends at 10:41.

Bandwidth Scaling
-----------------

AS automatically adjusts a bandwidth based on the scaling policies you configured.

After you configure a scaling policy as needed, when the trigger condition is met, AS automatically increases, decreases, or set the bandwidth to a specified value based on the policy you configured. Three types of bandwidth scaling policies are available, including the alarm, scheduled, and periodic policy.

Region
------

A region is a geographic area where the resources used by AS are located.

AZs in the same region can communicate with each other over an intranet, but AZs in different regions cannot.

Cloud data centers are deployed in locations around the world, including Europe and Asia, and AS applies to different regions. Deploying AS in different regions allows you to tailor policies to better suit your requirements. For example, applications can be designed to meet user requirements in specific regions or comply with local laws or regulations.

Project
-------

A project is used to group and isolate OpenStack resources, including compute, storage, and network resources. A project can be a department or a project team. Multiple projects can be created under one account.
