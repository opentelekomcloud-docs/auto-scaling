:original_name: as_faq_1206.html

.. _as_faq_1206:

Do I Need to Configure an EIP in an AS Configuration When a Load Balancer Has Been Enabled for an AS Group?
===========================================================================================================

No. If you have enabled a load balancer for an AS group, you do not have to configure an EIP in the AS configuration. The system automatically associates instances in the AS group to the load balancer. These instances will provide services via the EIP bound to the load balancer.
