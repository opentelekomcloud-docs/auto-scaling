:original_name: as_01_0107.html

.. _as_01_0107:

Deleting an AS Group
====================

Scenarios
---------

You can delete an AS group when it is no longer required.

-  If an AS group is not required during a specified period of time, you are advised to disable it but not delete it.
-  An AS group can be deleted only when it has no instances and no scaling action is being performed.
-  When an AS group is deleted, its AS policies and the alarm rules generated based those AS policies will be automatically deleted.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.
#. In the AS group list, locate the row containing the target AS group and choose **More** > **Delete** in the **Operation** column.
#. In the displayed **Delete AS Group** dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
