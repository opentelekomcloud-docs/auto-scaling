:original_name: as_04_0104.html

.. _as_04_0104:

Configuring an Instance Removal Policy
======================================

When instances are automatically removed from your AS group, the instances that are not in the currently used AZs will be removed first. Then the instance removal policy you select will be applied.

AS supports the following instance removal policies:

-  **Oldest instance**: The oldest instance is removed from the AS group first. Use this policy if you want to upgrade instances in an AS group to a new ECS type. You can gradually replace instances of the old type with instances of the new type.
-  **Newest instance**: The newest instance is removed from the AS group first. Use this policy if you want to test a new AS configuration but do not want to keep it in production.
-  **Oldest instance created from oldest AS configuration**: The oldest instance created from the oldest configuration is removed from the AS group first. Use this policy if you want to update an AS group and phase out the instances created from a previous AS configuration.
-  **Newest instance created from oldest AS configuration**: The newest instance created from the oldest configuration is removed from the AS group first.

.. note::

   Manually added instances are the last to be removed. If AS does remove a manually added instance, it only removes the instance. It does not delete the instance. If multiple manually added instances must be removed, AS preferentially removes the earliest-added instance first.
