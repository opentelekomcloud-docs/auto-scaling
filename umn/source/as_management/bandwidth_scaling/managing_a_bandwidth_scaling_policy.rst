:original_name: as_05_0103.html

.. _as_05_0103:

Managing a Bandwidth Scaling Policy
===================================

Scenarios
---------

You can adjust the bandwidth through a bandwidth scaling policy.

This section describes how to manage bandwidth scaling policies, including enabling, disabling, modifying, deleting, and immediately executing a bandwidth scaling policy.

.. note::

   The bandwidth scaling policy corresponding to a released EIP still occupies the policy quota. Only the account and its IAM users with the global permission can manage the AS bandwidth policy.

Enabling a Bandwidth Scaling Policy
-----------------------------------

A bandwidth scaling policy can be enabled only when its status is **Disabled**.

#. Log in to the management console.
#. Click |image1| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.
#. In the bandwidth scaling policy list, locate the row containing the target policy and click **Enable** in the **Operation** column.
#. In the displayed **Enable Bandwidth Scaling Policy** dialog box, click **Yes**.

Disabling a Bandwidth Scaling Policy
------------------------------------

A bandwidth scaling policy can be disabled only when its status is **Enabled**.

#. Log in to the management console.
#. Click |image2| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.
#. In the bandwidth scaling policy list, locate the row containing the target policy and click **Disable** in the **Operation** column.
#. In the displayed **Disable Bandwidth Scaling Policy** dialog box, click **Yes**.

   .. note::

      After a bandwidth scaling policy is disabled, its status changes to **Disabled**. AS does not automatically trigger any scaling action based on a **Disabled** bandwidth scaling policy.

Modifying a Bandwidth Scaling Policy
------------------------------------

#. Log in to the management console.
#. Click |image3| in the upper left corner to select a region and a project.

3. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.

4. In the bandwidth scaling policy list, locate the row containing the target policy and click the policy name to switch to its details page.

   Click **Modify** in the upper right corner of the page.

   You can also locate the row containing the target policy, click **More** in the **Operation** column, and select **Modify**.

5. Modify parameters. You can modify the following parameters of a bandwidth scaling policy: **Policy Name**, **EIP**, **Policy Type**, **Scaling Action**, and **Cooldown Period**.

6. Click **OK**.

.. note::

   A bandwidth scaling policy which is being executed cannot be modified.

Deleting a Bandwidth Scaling Policy
-----------------------------------

#. Log in to the management console.

#. Click |image4| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.

#. In the bandwidth scaling policy list, locate the row containing the target policy, click **More** in the **Operation** column, and select **Delete**.

#. In the displayed **Delete Bandwidth Scaling Policy** dialog box, click **Yes**.

   You can also select one or more scaling policies and click **Delete** above the list to delete one or more scaling policies.

.. note::

   -  You can delete a bandwidth scaling policy when you no longer need it. If you do not need it only during a specified period of time, you are advised to disable rather than delete it.
   -  A bandwidth scaling policy can be deleted only when it is not being executed.

Executing a Bandwidth Scaling Policy
------------------------------------

By executing a bandwidth scaling policy, you can immediately adjust the bandwidth to that configured in the bandwidth scaling policy, instead of having to wait until the trigger condition is met.

#. Log in to the management console.
#. Click |image5| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.
#. In the bandwidth scaling policy list, locate the row that contains the target policy and click **Execute Now** in the **Operation** column.
#. In the displayed **Execute Bandwidth Scaling Policy** dialog box, click **Yes**.

You can also go to the bandwidth scaling policy details page and click **Execute Now** in the upper right corner.

.. note::

   -  A bandwidth scaling policy can be executed only when the policy is enabled and no other bandwidth scaling policy is being executed.
   -  Executing a bandwidth scaling policy does not affect automatic adjustment of the bandwidth when the trigger condition of the policy is met.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210485079.png
.. |image3| image:: /_static/images/en-us_image_0210485079.png
.. |image4| image:: /_static/images/en-us_image_0210485079.png
.. |image5| image:: /_static/images/en-us_image_0210485079.png
