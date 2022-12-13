:original_name: as_faq_1201.html

.. _as_faq_1201:

What Operations Will Be Suspended If an AS Group Is Disabled?
=============================================================

If an AS group is disabled, new scaling actions will not happen, but any scaling actions already in progress will continue. Scaling policies will not trigger any scaling actions. Even if you manually change the number of expected instances, no scaling action will be triggered even though the number of actual instances is not equal to that of expected instances.

Health checks continue to be performed but will not remove any instances.
