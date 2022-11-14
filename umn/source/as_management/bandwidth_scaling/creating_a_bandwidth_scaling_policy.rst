:original_name: en-us_topic_0112331243.html

.. _en-us_topic_0112331243:

Creating a Bandwidth Scaling Policy
===================================

Scenarios
---------

You can automatically adjust your purchased EIP bandwidth and shared bandwidth using a bandwidth scaling policy. This section describes how to create a bandwidth scaling policy.

When creating a bandwidth scaling policy, you need to configure basic information. The system supports three types of bandwidth scaling policies: alarm-based, scheduled, and periodic.

The basic information for creating a bandwidth scaling policy includes the policy name, policy type, and trigger condition.

Creating an Alarm-based Bandwidth Scaling Policy
------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.

#. Click **Create Bandwidth Scaling Policy**.

#. Set parameters, such as the policy name, policy type, and trigger condition. For details, see :ref:`Table 1 <en-us_topic_0112331243__table1795013419434>`.

   .. _en-us_topic_0112331243__table1795013419434:

   .. table:: **Table 1** Alarm policy parameters

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                    | Example Value         |
      +=======================+================================================================================================================================================================================================================================================+=======================+
      | Region                | Specifies the region where the AS group resides.                                                                                                                                                                                               | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Policy Name           | Specifies the name of the bandwidth scaling policy.                                                                                                                                                                                            | N/A                   |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | The name consists of only letters, digits, underscores (_), and hyphens (-).                                                                                                                                                                   |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | EIP                   | Specifies the public network IP address whose bandwidth needs to be scaled.                                                                                                                                                                    | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Policy Type           | Select **Alarm**.                                                                                                                                                                                                                              | Alarm                 |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Alarm Rule            | You can use an existing alarm rule or create a new one.                                                                                                                                                                                        | N/A                   |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | To create an alarm rule, configure the following parameters:                                                                                                                                                                                   |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Rule Name                                                                                                                                                                                                                                   |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    Specifies the name of the new alarm rule, for example, **as-alarm-7o1u**.                                                                                                                                                                   |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Trigger Condition                                                                                                                                                                                                                           |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    Select a monitoring metric and trigger condition based on the metric. :ref:`Table 2 <en-us_topic_0112331243__table46471722185419>` lists the supported monitoring metrics. An example value is **Outbound Bandwidth** **Avg. > 100 bit/s**. |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Monitoring Interval                                                                                                                                                                                                                         |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    Specifies the period for the metric, for example, 5 minutes.                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Consecutive Occurrences                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    Specifies the number of consecutive times, for example, one time, for triggering a scaling action during a monitoring period.                                                                                                               |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Scaling Action        | Specifies the execution action in the AS policy.                                                                                                                                                                                               | N/A                   |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | The following scaling action options are available:                                                                                                                                                                                            |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Add                                                                                                                                                                                                                                         |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    When a scaling action is triggered, the bandwidth is increased.                                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Reduce                                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    When a scaling action is triggered, the bandwidth is decreased.                                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       | -  Set to                                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    The bandwidth is set to a fixed value.                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |    .. note::                                                                                                                                                                                                                                   |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |       The step (minimum unit for bandwidth adjustment) varies depending on the bandwidth value range. The bandwidth will be automatically adjusted to the nearest value according to the actual step.                                          |                       |
      |                       |                                                                                                                                                                                                                                                |                       |
      |                       |       -  If the bandwidth is less than or equal to 300 Mbit/s, the default step is 1 Mbit/s.                                                                                                                                                   |                       |
      |                       |       -  If the bandwidth ranges from 300 Mbit/s to 500 Mbit/s, the default step is 50 Mbit/s.                                                                                                                                                 |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Cooldown Period       | Specifies a period of time in the unit of second after each scaling action is complete. During the cooldown period, scaling actions triggered by alarms will be denied. Scheduled and periodic scaling actions are not restricted.             | 300s                  |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   .. _en-us_topic_0112331243__table46471722185419:

   .. table:: **Table 2** Monitoring metrics supported by the alarm policy

      +--------------------+----------------------------------------------------------------+
      | Metric             | Description                                                    |
      +====================+================================================================+
      | Inbound Bandwidth  | Indicates the network rate of inbound traffic.                 |
      +--------------------+----------------------------------------------------------------+
      | Inbound Traffic    | Indicates the network traffic going into the cloud platform.   |
      +--------------------+----------------------------------------------------------------+
      | Outbound Bandwidth | Indicates the network rate of outbound traffic.                |
      +--------------------+----------------------------------------------------------------+
      | Outbound Traffic   | Indicates the network traffic going out of the cloud platform. |
      +--------------------+----------------------------------------------------------------+

#. After setting the parameters, click **Create Now**.

   The newly created bandwidth scaling policy is displayed on the **Bandwidth Scaling** page and is in **Enabled** state by default.

Creating a Scheduled or Periodic Bandwidth Scaling Policy
---------------------------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.

#. Click **Create Bandwidth Scaling Policy**.

#. Set parameters, such as the policy name, policy type, and trigger condition. For details, see :ref:`Table 3 <en-us_topic_0112331243__table085923816615>`.

   .. _en-us_topic_0112331243__table085923816615:

   .. table:: **Table 3** Scheduled or periodic policy parameters

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                        | Example Value         |
      +=======================+====================================================================================================================================================================================================================================+=======================+
      | Region                | Specifies the region where the AS group resides.                                                                                                                                                                                   | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Policy Name           | Specifies the name of the bandwidth scaling policy.                                                                                                                                                                                | as-policy-p6g5        |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | The name consists of only letters, digits, underscores (_), and hyphens (-).                                                                                                                                                       |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | EIP                   | Specifies the public network IP address whose bandwidth needs to be scaled. This parameter is mandatory when **Resource Type** is set to **EIP**.                                                                                  | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Policy Type           | Specifies the policy type. You can select a scheduled or periodic policy.                                                                                                                                                          | N/A                   |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | If you select **Periodic**, you are required to configure two more parameters:                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Time Range                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    Specifies a time range during which the AS policy can be triggered.                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Interval                                                                                                                                                                                                                        |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    -  One day                                                                                                                                                                                                                      |                       |
      |                       |    -  One week                                                                                                                                                                                                                     |                       |
      |                       |    -  One month                                                                                                                                                                                                                    |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Triggered At          | Specifies a time at which the AS policy is triggered.                                                                                                                                                                              | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Scaling Action        | Specifies the action to be performed.                                                                                                                                                                                              | N/A                   |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | The following scaling action options are available:                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Add                                                                                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    When a scaling action is triggered, the bandwidth is increased.                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Reduce                                                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    When a scaling action is triggered, the bandwidth is decreased.                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Set to                                                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    The bandwidth is set to a fixed value.                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    .. note::                                                                                                                                                                                                                       |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |       The step (minimum unit for bandwidth adjustment) varies depending on the bandwidth value range. The bandwidth will be automatically adjusted to the nearest value according to the actual step.                              |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |       -  If the bandwidth is less than or equal to 300 Mbit/s, the default step is 1 Mbit/s.                                                                                                                                       |                       |
      |                       |       -  If the bandwidth ranges from 300 Mbit/s to 500 Mbit/s, the default step is 50 Mbit/s.                                                                                                                                     |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Cooldown Period       | Specifies a period of time in the unit of second after each scaling action is complete. During the cooldown period, scaling actions triggered by alarms will be denied. Scheduled and periodic scaling actions are not restricted. | 300s                  |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. After setting the parameters, click **Create Now**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210485079.png
