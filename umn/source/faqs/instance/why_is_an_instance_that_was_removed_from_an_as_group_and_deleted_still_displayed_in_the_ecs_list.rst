:original_name: as_faq_0040.html

.. _as_faq_0040:

Why Is an Instance that Was Removed from an AS Group and Deleted Still Displayed in the ECS List?
=================================================================================================

If an automatically added instance is protected, it is removed out of the AS group but not deleted, so that it can still be used by other services.

An instance that is being used by other services are protected generally. For example, an instance is used by IMS for creating a private image, or used by SDRS.
