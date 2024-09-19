:original_name: as_04_0107.html

.. _as_04_0107:

Configuring Instance Protection
===============================

Scenarios
---------

To control whether an instance can be removed automatically from an AS group, use instance protection. Once configured, when AS automatically scales in the AS group, the instance that is protected will not be removed.

Prerequisites
-------------

Instance protection does not protect instances from the following:

-  Health check replacement if the instance fails health checks
-  Manual removal

   .. note::

      -  Instance protection does not protect unhealthy instances because such instances cannot provide services.
      -  By default, instance protection does not take effect on the ECSs that are newly created in or added to an AS group.
      -  If an instance is removed from an AS group, its instance protection setting is lost.

Enabling Instance Protection
----------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.
#. Click the name of the target AS group.
#. Click the **Instances** tab. Select one or more instances and choose **Enable Instance Protection** from the **More** drop-down list. In the displayed **Enable Instance Protection** dialog box, click **Yes**.

Disabling Instance Protection
-----------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select the desired region and project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.
#. Click the name of the target AS group.
#. Click the **Instances** tab. Select one or more instances and choose **Disable Instance Protection** from the **More** drop-down list. In the displayed **Disable Instance Protection** dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210485079.png
