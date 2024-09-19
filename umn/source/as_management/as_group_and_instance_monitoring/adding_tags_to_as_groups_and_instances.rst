:original_name: as_06_0104.html

.. _as_06_0104:

Adding Tags to AS Groups and Instances
======================================

Scenarios
---------

If you have many resources of the same type, you can use tags to manage resources flexibly. You can identify specified resources quickly using the tags allocated to them.

Using a tag, you can assign custom data to each AS group. You can organize and manage AS groups, for example, classify AS group resources by usage, owner, or environment.

Each tag contains a key and a value. You can specify the key and value for each tag. A key can be a category associated with certain values, such as usage, owner, and environment.

For example, if you want to distinguish between the test environment and production environment, you can allocate a tag with the key **environment** to each AS group. For the test environment, the key value is **test** and for the production environment, the key value is **production**. You are advised to use one or more groups of consistent tags to manage your AS group resources.

After you allocate a tag to an AS group, the system will automatically add the tag to the instances automatically created in the AS group. If you add a tag to an AS group or modify the tag, the new tag will be added to the ECSs automatically created in the AS group. Creating, deleting, or modifying the tag of an AS group will have no impact on the ECSs in the AS group.

Restrictions of Using Tags
--------------------------

You must observe the following rules when using tags:

-  Each AS group can have a maximum of 10 tags added to it.
-  Each tag contains a key and a value.
-  You can set the tag value to an empty character string.
-  If you delete an AS group, all tags of it will also be deleted.

Adding a Tag to an AS Group
---------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.

#. Click the AS group name. On the AS group details page, click the **Tags** tab and then click **Add Tag**.

#. Set the parameters listed in :ref:`Table 1 <as_06_0104__table1794599823119>`.

   .. _as_06_0104__table1794599823119:

   .. table:: **Table 1** Tag naming rules

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirement                                                                                                              | Example Value         |
      +=======================+==========================================================================================================================+=======================+
      | Tag Key               | -  The value cannot be empty.                                                                                            | Organization          |
      |                       | -  The key must be unique to the AS group.                                                                               |                       |
      |                       | -  A key can contain a maximum of 36 characters, including only digits, letters, hyphens (-), and underscores (_).       |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag Value             | -  The value is optional.                                                                                                | Apache                |
      |                       | -  A key can have only one value.                                                                                        |                       |
      |                       | -  A tag value can contain a maximum of 43 characters, including only digits, letters, hyphens (-), and underscores (_). |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

Modifying or Deleting Tags of an AS Group
-----------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.

#. Click the AS group name. On the **Overview** page, click the **Tags** tab.

#. Locate the row that contains the tag and click **Edit** or **Delete** in the **Operation** column.

   After clicking **Edit**, configure required parameters. For details, see :ref:`Table 1 <as_06_0104__table1794599823119>`.

   After you click **Delete**, the added tag will be deleted.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210485079.png
