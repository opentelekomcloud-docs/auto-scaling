:original_name: as_faq_0012.html

.. _as_faq_0012:

Why Can't I Use a Key File to Log In to an ECS?
===============================================

Issue Description
-----------------

When I used a key file to attempt to log in to an instance in an AS group, the login failed.

Possible Causes
---------------

The image specified in the AS configuration of the AS group is a private image, on which Cloud-Init has not been installed.

In this case, it would not be possible to customize the ECS configuration. As a result, you can log in to the ECS only using the original image password or key pair.

Handling Method
---------------

#. Check whether the ECS needs to be logged in to.

   -  If yes, use the original image password or key pair to log in to this ECS.

      The original image password or key pair is the OS password or key pair configured when the private image was created.

   -  If no, go to step :ref:`2 <as_faq_0012__li4126846117151>`.

#. .. _as_faq_0012__li4126846117151:

   Change the AS configuration of the AS group. For details, see :ref:`Changing the AS Configuration for an AS Group <as_01_0103>`.

.. note::

   Make sure that Cloud-Init or Cloudbase-Init has been installed on the image specified in the new AS configuration. For how to install Cloud-Init or Cloudbase-Init, see *Image Management Service User Guide*.

After the AS configuration is changed, you can use the key file to log in to the new ECSs that are added to the AS group during scaling actions. You do not need to use the original image password or key pair to log in to these new ECSs anymore.
