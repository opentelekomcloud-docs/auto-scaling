:original_name: en-us_topic_0042018380.html

.. _en-us_topic_0042018380:

Managing Lifecycle Hooks
========================

Lifecycle hooks enable you to flexibly control addition and removal of ECS instances in AS groups and manage the lifecycle of ECS instances in AS groups. :ref:`Figure 1 <en-us_topic_0042018380__fig9892349365>` shows the instance lifecycle when no lifecycle hook is added to an AS group.

.. _en-us_topic_0042018380__fig9892349365:

.. figure:: /_static/images/en-us_image_0000001763445960.png
   :alt: **Figure 1** Instance lifecycle when no lifecycle hook is added to an AS group

   **Figure 1** Instance lifecycle when no lifecycle hook is added to an AS group

:ref:`Figure 2 <en-us_topic_0042018380__fig18177642182519>` shows the instance lifecycle when a lifecycle hook is added to an AS group.

.. _en-us_topic_0042018380__fig18177642182519:

.. figure:: /_static/images/en-us_image_0000002040045537.png
   :alt: **Figure 2** Instance lifecycle when a lifecycle hook is added to an AS group

   **Figure 2** Instance lifecycle when a lifecycle hook is added to an AS group

When the AS group scales in or out, the added lifecycle hooks are triggered, the scaling action is suspended, and the instance being added or removed is put into a wait state, as shown in 2 and 6 in :ref:`Figure 2 <en-us_topic_0042018380__fig18177642182519>`. During this period of time, you can perform some custom operations on the instance. For example, you can install or configure software on an instance being added to the AS group. A suspended scaling action will be resumed if either of the following occurs:

-  The timeout duration ends.

   Assume that you have set the timeout period to 3,600s by referring to section :ref:`Table 1 <en-us_topic_0042018380__table14431103919157>`. The suspended scaling action will be automatically resumed if the timeout duration (3,600s) ends.

-  A callback action is performed to move the instance out of the wait state. For details, see :ref:`Performing a Callback Action <en-us_topic_0042018380__section01303241231>`.

Application Scenarios
---------------------

-  Instances newly added to an AS group need to be initialized before they are bound to a load balancer listener. Initialization means the software is installed and configured and the instance is fully ready to accept traffic.
-  To remove an instance from an AS group, it needs to be first unbound from the load balancer listener, stop accepting new requests, and finish processing any accepted requests.
-  Before instances are removed from an AS group, you may need to back up data or download logs.
-  Other scenarios where custom operations need to be performed.

How Lifecycle Hooks Work
------------------------

After you add lifecycle hooks to an AS group, they work as follows:

-  Adding an ECS instance to an AS group

   When an instance is initialized and added to an AS group, a lifecycle hook of the **Instance adding** type is automatically triggered. The instance enters the **Wait (Adding to AS group)** state, that is, the instance is suspended by the lifecycle hook. If you have configured a notification object, the system sends a message to the object. After receiving the message, you can perform custom operations, for example, installing software on the instance. The instance remains in a wait state until you complete the custom operations and perform a callback action (see :ref:`Performing a Callback Action <en-us_topic_0042018380__section01303241231>`) or the timeout duration ends. After the instance moves out of a wait state, the specified default callback action will take place.

   -  **Continue**: The instance will be added to the AS group.
   -  **Abandon**: The instance will be deleted and a new instance will be created.

   If you have configured multiple **Instance adding** lifecycle hooks, all of them will be triggered when an instance is added to the AS group. If the default callback action of any lifecycle hook is **Abandon**, the instance will be deleted and a new instance will be created. If the default callback action of all lifecycle hooks is **Continue**, the instance is added to the AS group after suspension by the last lifecycle hook is complete.

-  Removing an instance from an AS group

   When an instance is removed from an AS group, the instance enters the **Removing** state. After a lifecycle hook is triggered, the instance enters the **Wait (Removing from AS group)** state. The system sends messages to the configured notification object. After receiving the message, you can perform custom operations, such as uninstalling software and backing up data. The instance remains in the wait state until you finish the custom operations and perform the default callback operation or the timeout duration ends. After the instance moves out of a wait state, the specified default callback action will take place.

   -  **Continue**: The instance is removed from the AS group.
   -  **Abandon**: The instance is removed from the AS group.

   If you have configured multiple lifecycle hooks, and the default callback action of all lifecycle hooks is **Continue**, the instance will be removed from the AS group until suspension by the remaining lifecycle hooks time out. If the default callback action of any lifecycle hook is **Abandon**, the instance will be directly removed from the AS group.

Constraints
-----------

-  You can add, modify, or delete a lifecycle hook when the AS group does not perform a scaling action.
-  Up to five lifecycle hooks can be added to one AS group.

Adding a Lifecycle Hook
-----------------------

#. Log in to the management console.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.

#. Click the name of the AS group to which the lifecycle hook is to be added. On the AS group details page, click the **Lifecycle Hooks** tab and then **Add Lifecycle Hook**.

#. In the displayed **Add Lifecycle Hook** dialog box, set the parameters listed in :ref:`Table 1 <en-us_topic_0042018380__table14431103919157>`.

   .. _en-us_topic_0042018380__table14431103919157:

   .. table:: **Table 1** Parameter description

      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                              | Example Value         |
      +=========================+==========================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Hook Name               | Specifies the lifecycle hook name. The name can contain letters, digits, underscores (_), and hyphens (-), and cannot exceed 32 characters.                                                                                                                                                                                                                                              | we12_w                |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Hook Type               | Specifies the lifecycle hook type. The value can be **Instance adding** or **Instance removal**. **Instance adding** puts the instance being added to an AS group to the **Wait (Adding to AS group)** state. **Instance removal** puts the instance being removed from an AS group to **Wait (Removing from AS group)** state.                                                          | Instance adding       |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Default Callback Action | Specifies the action that the system takes when an instance moves out of a wait state.                                                                                                                                                                                                                                                                                                   | Continue              |
      |                         |                                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                         | The default callback action for an **Instance adding** lifecycle hook can be **Continue** or **Abandon**:                                                                                                                                                                                                                                                                                |                       |
      |                         |                                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                         | -  **Continue**: If multiple lifecycle hooks are configured for the AS group, and the default callback action of all the hooks is **Continue**, the system will continue to add the instance to the AS group until the all lifecycle hooks time out.                                                                                                                                     |                       |
      |                         | -  **Abandon**: If multiple lifecycle hooks are configured for the AS group, and the default callback action of one lifecycle hook is **Abandon**, the system will delete the instance and create another one without waiting for the remaining lifecycle hooks to time out.                                                                                                             |                       |
      |                         |                                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                         | The default callback action for an **Instance removal** lifecycle hook can be **Continue** or **Abandon**:                                                                                                                                                                                                                                                                               |                       |
      |                         |                                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                         | -  **Continue**: If only one lifecycle hook is configured for the AS group, the system will remove the instance from the AS group. If multiple lifecycle hooks are configured for the AS group, and the default callback actions of all the hooks are **Continue**, the system will continue to remove the instance from the AS group until all lifecycle hooks time out.                |                       |
      |                         | -  **Abandon**: If multiple lifecycle hooks are configured for the AS group, and the default callback action of one lifecycle hook is **Abandon**, the system will continue to remove the instance from the AS group without waiting for the remaining lifecycle hooks to time out.                                                                                                      |                       |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Timeout Duration (s)    | Specifies the amount of time for the instances to remain in a wait state. The value ranges from 60s to 86,400s.                                                                                                                                                                                                                                                                          | 3600                  |
      |                         |                                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                         | You can extend the timeout duration or perform a **Continue** or **Abandon** action before the timeout duration ends. For more information about callback actions, see :ref:`Performing a Callback Action <en-us_topic_0042018380__section01303241231>`.                                                                                                                                 |                       |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Notification Topic      | Specifies a notification object for a lifecycle hook. For details, see "Creating a Topic" in *Simple Message Notification User Guide*. When an instance is suspended by the lifecycle hook, the system sends a notification to the object. This notification contains the basic instance information, your custom notification content, and the token for controlling lifecycle actions. | N/A                   |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Notification Message    | After a notification object is configured, the system sends your custom notification to the object.                                                                                                                                                                                                                                                                                      | ``-``                 |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   The added lifecycle hook is displayed on the **Lifecycle Hooks** page.

.. _en-us_topic_0042018380__section01303241231:

Performing a Callback Action
----------------------------

#. On the **AS Groups** page, click the name of the target AS group.

#. On the displayed page, click the **Instances** tab.

#. Locate the instance that has been suspended by the lifecycle hook and click **Wait (Adding to AS group)** or **Wait (Removing from AS group)** in the **Lifecycle Status** column.

   .. note::

      Callback actions can only be performed on instances that have been suspended by a lifecycle hook.

#. In the displayed **Added Hook** dialog box, view the suspended instance and all the lifecycle hooks, and perform callback actions on lifecycle hooks.

   Callback actions include:

   -  **Continue**
   -  **Abandon**
   -  **Extend timeout**

   If you have performed custom operations before the timeout duration ends, select **Continue** or **Abandon** to complete the lifecycle actions. For details about **Continue** and **Abandon**, see :ref:`Table 1 <en-us_topic_0042018380__table14431103919157>`. If you need more time for custom operations, select **Extend timeout** to extend the timeout duration. Then, the timeout duration will be extended by 3600 seconds each time.

Modifying a Lifecycle Hook
--------------------------

On the **Lifecycle Hooks** page, locate the target lifecycle hook and click **Modify** in the **Operation** column, see :ref:`Table 1 <en-us_topic_0042018380__table14431103919157>` for parameters. You can modify the parameter except **Hook Name**, such as **Hook Type**, **Default Callback Action**, and **Timeout Duration**.

Deleting a Lifecycle Hook
-------------------------

On the **Lifecycle Hooks** page, locate the target lifecycle hook and click **Delete** in the **Operation** column.
