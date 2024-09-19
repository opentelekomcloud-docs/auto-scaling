:original_name: en-us_topic_0042018362.html

.. _en-us_topic_0042018362:

Creating an AS Configuration
============================

An AS configuration defines the specifications of the ECS instances to be added to an AS group. The specifications include the ECS image and system disk size.

Scenarios
---------

-  When you create an AS group, create a new AS configuration or use an existing AS configuration.
-  Create the required AS configuration on the **Instance Scaling** page.
-  Change the AS configuration on the AS group details page.

Methods
-------

-  Create an AS configuration from an existing ECS instance.

   If you create an AS configuration from an existing ECS instance, the vCPU, memory, image, disk, and ECS type are the same as those of the selected instance by default. For details, see :ref:`Creating an AS Configuration from an Existing ECS <as_02_0102>`.

-  Create an AS configuration from a new specifications template.

   If you have special requirements on the ECSs for resource expansion, use a new specifications template to create the AS configuration. For details, see :ref:`Creating an AS Configuration from Scratch <as_02_0103>`.
