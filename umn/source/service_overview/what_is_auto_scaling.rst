:original_name: en-us_topic_0042018383.html

.. _en-us_topic_0042018383:

What Is Auto Scaling?
=====================

AS Introduction
---------------

Auto Scaling (AS) helps you automatically scale Elastic Cloud Server (ECS) and bandwidth resources to keep up with changes in demand based on pre-configured AS policies. It allows you to add ECS instances or increase bandwidths to handle load increases and also save money by removing resources that are sitting idle.

Architecture
------------

AS allows you to scale ECS instances and bandwidths.

-  Scaling control: You can configure AS policies, configure metric thresholds, and schedule when different scaling actions are taken. AS will trigger scaling actions on a repeating schedule, at a specific time, or when the configured thresholds are reached.
-  Policy configuration: You can configure alarm-based, scheduled, and periodic policies as needed.
-  Alarm-based policies: You can configure scaling actions to be taken when alarm metrics such as vCPU, memory, disk, and inbound traffic reach the thresholds.
-  Scheduled policies: You can schedule scaling actions to be taken at a specific time.
-  Periodic policies: You can configure scaling actions to be taken at scheduled intervals, at specific time, or within a particular time range.
-  When Cloud Eye generates an alarm for a monitoring metric, for example, CPU usage, AS automatically increases or decreases the number of instances in the AS group or the bandwidths.
-  When the configured triggering time arrives, a scaling action is triggered to increase or decrease the number of ECS instances or the bandwidths.


.. figure:: /_static/images/en-us_image_0284722761.png
   :alt: **Figure 1** AS architecture

   **Figure 1** AS architecture

Accessing AS
------------

The public cloud provides a web-based service management platform. You can access AS using HTTPS-compliant application programming interfaces (APIs) or the management console.

-  Calling APIs

   Use this method if you are required to integrate AS on the public cloud into a third-party system for secondary development. For more information, see *Auto Scaling API Reference*.

-  Management console

   Use this method if you do not need to integrate AS with a third-party system.

   After registering on the public cloud, log in to the management console and select **Auto Scaling** from the service list on the homepage.
