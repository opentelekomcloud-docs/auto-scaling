:original_name: as_06_0106.html

.. _as_06_0106:

Viewing Monitoring Metrics
==========================

Scenarios
---------

The cloud platform provides Cloud Eye to help you obtain the running status of your ECS instances. This section describes how to view details of AS group metrics to obtain information about the status of the ECS instances in the AS group.

Prerequisites
-------------

The ECS instance is running properly.

.. note::

   -  Monitoring metrics such as **CPU Usage** and **Disks Read Rate** are available only when there is at least one instance in an AS group. If not, only the **Number of Instances** metric is available.
   -  Monitoring data is not displayed for a stopped, faulty, or deleted instance. After such an instance restarts or recovers, the monitoring data is available.

Viewing Monitoring Metrics on Auto Scaling
------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.

#. On the **AS Groups** page, find the AS group to view monitoring data and click its name.

#. Click the **Monitoring** tab to view the monitoring data.

   You can view data of the last one, three, 12, or 24 hours, or last 7 days. If you want to view data for a longer time range, click **View details** to go to the **Cloud Eye** page, hover your mouse over a graph, and click |image2|.

Viewing Monitoring Metrics on Cloud Eye
---------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner to select a region and a project.

#. Under **Management & Deployment**, select **Cloud Eye**.

#. In the navigation pane on the left, choose **Cloud Service Monitoring** > **Auto Scaling**.

#. Locate the row that contains the target AS group and click **View Metric** in the **Operation** column to view monitoring data.

   You can view data of the last one, three, 12, or 24 hours, or last 7 days. Hover your mouse over a graph and click |image4| to view data for a longer time range.

.. note::

   It can take a period of time to obtain and transfer the monitoring data. Therefore, wait for a while and then check the data.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210500918.png
.. |image3| image:: /_static/images/en-us_image_0210485079.png
.. |image4| image:: /_static/images/en-us_image_0210500918.png
