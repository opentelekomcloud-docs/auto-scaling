:original_name: as_faq_0030.html

.. _as_faq_0030:

How Do I Handle Unhealthy Instances in an AS Group?
===================================================

Normally, you do not need to handle unhealthy instances because AS periodically checks the health status of instances in an AS group. When an AS group is enabled, unhealthy instances are removed and new instances are created to ensure that the expected number of instances are running in the AS group. When an AS group is disabled, AS still checks the health of instances, but does not remove instances.

It should be noted that if ELB health check is selected, ELB sends heartbeat messages to instances through an intranet. To ensure that the ELB health check can be performed properly, ensure that your instances can be accessed through that intranet. To check this, perform the following steps:

#. .. _as_faq_0030__li25183589153427:

   In the **Listener** area, locate the row containing the target listener and click **View** in the **Health Check** column. A dialog box is displayed.

   -  **Health Check Protocol**: Ensure that the protocol has been configured and port has been enabled for the ECS instance to be checked.
   -  **Check Path**: If HTTP is used for the health check, ensure that the health check path for the instance is correct.

#. Confirm that there is no software such as firewall on the instance blocking the source IP address used for performing the health check.

#. Confirm that the rules of instance security groups and network ACL allow access from 100.125.0.0/16, and configure the protocol and port used for health check. Obtain the health check protocol and port from the dialog box displayed in step :ref:`1 <as_faq_0030__li25183589153427>`.

   -  If the default type of health check is used, service ports of the instances must be enabled.
   -  If the health check port is different from service ports of the instances, communication between the service ports and health check port must be enabled.

#. If the issue persists, contact technical support.
