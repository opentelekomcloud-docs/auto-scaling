:original_name: as_faq_0033.html

.. _as_faq_0033:

How Do I Fix the Error "The key pair does not exist" When I Connect to an Instance?
===================================================================================

A key pair is specific to each user. If the key pair of a user who belongs to the same account as you is configured for an AS configuration, you cannot connect the instances scaled out using that AS configuration.

If you want to connect to these instances without being restricted by the key pair permission, password authentication needs to be configured as the login mode.
