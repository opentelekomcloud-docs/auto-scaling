:original_name: as_02_0101.html

.. _as_02_0101:

Setting Up an Automatically Scalable Discuz! Forum
==================================================

Overview
--------

AS automatically adds instances to an AS group for applications and removes unneeded ones on demand. You do not need to prepare a large number of extra ECS instances for expected marketing activities or unexpected peak hours. By eliminating the need to deploy those extra instances, AS ensures system reliability and reduces your operating costs.

This section describes how to use services, such as AS, ECS, ELB, and VPC to deploy a web service that can be automatically scaled in and out, for example, a Discuz! forum.

|image1|

Prerequisites
-------------

#. .. _as_02_0101__li141420388395:

   A VPC, subnet, security group, and EIP are available.

2. A load balancer and listener have been created. The VPC obtained in :ref:`1 <as_02_0101__li141420388395>` is selected during the load balancer creation.

Procedure
---------

**Create an ECS and install a MySQL database.**

You can create a relational database using the Relational Database Service (RDS) service provided by the cloud platform, or create an ECS and install the database there. In this section, we will install a MySQL database on a newly created ECS.

#. Use the created VPC, security group, and EIP for the ECS you create. For instructions about how to create an ECS, see *Elastic Cloud Server User Guide*.
#. When the status of the ECS changes to **Running**, use Xftp or Xshell to log in to the ECS through its EIP, and install and configure a MySQL database.

**Create an ECS and deploy a Discuz! forum on it.**

#. Create an ECS but do not bind an EIP to it. For instructions about how to create an ECS, see *Elastic Cloud Server User Guide*.

#. Unbind the EIP from the ECS where the MySQL database is installed and bind the EIP to the ECS where the Discuz! forum is to be deployed.

   You can access the MySQL database through a private network, so the EIP bound to the ECS where the MySQL database is installed can be unbound and then bound to the ECS where the Discuz! forum is to be deployed. This improves resource utilization. For detailed operations, see *Virtual Private Cloud User Guide*. After binding the EIP, you can access the ECS from the Internet and install various environments, such as PHP and Apache.

#. Deploy the forum.

   To learn how to deploy the Discuz! forum, see the officially released Discuz! documentation. When configuring parameters, configure the private IP address of the ECS where the MySQL database is installed for the database server, and use the username and password authorized for remotely accessing the ECS where the MySQL database is installed to access the MySQL database. After the configuration is complete, you can unbind the EIP from the ECS where the forum is deployed to reduce resource usage.

**Create a private image.**

Use the ECS where the Discuz! forum is deployed to create a private image. This private image is used to create the ECSs that will be used for capacity expansion.

#. Only a stopped ECS can be used to create a private image. Stop the ECS where the Discuz! forum is deployed before creating a private image. For detailed operations, see *Elastic Cloud Server User Guide*.
#. Use the ECS to create a private image. For details, see *Image Management Service User Guide*.

**Create an AS group.**

An AS group is a collection of ECS instances with the same configurations and AS policies that have similar attributes and apply to the same application scenario. An AS group is the basis for enabling or disabling AS policies and performing scaling actions. You must create an AS group to automatically add or remove ECS instances to match changes in traffic to the Discuz! forum.

For instructions about how to create an AS group, see :ref:`Creating an AS Group <en-us_topic_0042018368>`. During the configuration, use the created VPC, subnet, load balancer, and listener.

**Create an AS configuration.**

The AS configuration lists the basic specifications of the ECSs to be automatically added to the AS group in a scaling action.

For instructions about how to create an AS configuration, see :ref:`Creating an AS Configuration from Scratch <as_02_0103>`. During the configuration, select the private image you created in the preceding step. Configure other parameters based on service requirements.

**Manually add the ECS to the AS group.**

On the page providing details about the AS group, click the **Instances** tab and then **Add** to add the ECS where the Discuz! forum is deployed to the AS group. For details, see :ref:`Manual Scaling <as_04_0103>`. You can enable instance protection for this ECS so that it will not be automatically removed from the AS group.

**Create an AS policy.**

An AS policy specifies the conditions for triggering a scaling action. After you create an AS policy for the AS group, AS automatically increases or decreases the number of instances based on the policy.

You can configure an alarm-based AS policy. When Cloud Eye generates an alarm for a monitoring metric, such as vCPU usage, AS automatically increases or decreases the number of instances in the AS group. If traffic fluctuations are predictable, you can also configure a scheduled or periodic AS policy.

For instructions about how to create an AS policy, see :ref:`Dynamic Scaling <as_04_0101>` and :ref:`Scheduled Scaling <as_04_0102>`. After an AS policy is created and enabled, if a triggering condition is met, the AS group scales in or out as needed.

.. |image1| image:: /_static/images/en-us_image_0077278626.png
