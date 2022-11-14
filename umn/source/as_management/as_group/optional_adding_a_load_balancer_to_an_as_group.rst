:original_name: as_01_0102.html

.. _as_01_0102:

(Optional) Adding a Load Balancer to an AS Group
================================================

Elastic Load Balancing (ELB) automatically distributes incoming traffic across multiple backend servers based on configured forwarding policies. ELB expands the service capabilities of applications and improves their availability by eliminating single points of failure (SPOFs).

If ELB functions are required, perform the operations provided in this section to add a load balancer to your AS group. The load balancer added to an AS group distributes application traffic to all instances in the AS group when an instance is added to or deleted from the AS group.

Only a created load balancer can be bound to an AS group, and the AS group and load balancer must be in the same VPC. For details about how to create a load balancer, see *Elastic Load Balancing User Guide*. To add a load balancer for an AS group, perform the following operations:

-  When creating an AS group, configure parameter **Load Balancing** to add a load balancer. For details, see :ref:`Creating an AS Group <en-us_topic_0042018368>`.
-  If the AS group is not enabled, contains no instance, and has no scaling action ongoing, you can modify **Load Balancing** to add a load balancer for the AS group. For details, see :ref:`Modifying an AS Group <as_01_0106>`.
