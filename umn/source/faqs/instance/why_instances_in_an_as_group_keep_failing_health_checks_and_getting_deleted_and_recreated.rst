:original_name: as_faq_1205.html

.. _as_faq_1205:

Why Instances in an AS Group Keep Failing Health Checks and Getting Deleted and Recreated?
==========================================================================================

The rules of security group that the instances are in must allow access from the 100.125.0.0/16 network segment over the protocol and port used by ELB for health checks, or the health checks will fail. As a result, the instances will be deleted and created again and again.
