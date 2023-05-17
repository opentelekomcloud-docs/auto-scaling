:original_name: as_faq_0011.html

.. _as_faq_0011:

How Can I Automatically Deploy My Application on an Instance?
=============================================================

To enable automatic application deployment on instances automatically added to an AS group, create a private image with the application preinstalled and automatic startup settings preconfigured. Create an AS configuration with the private image, and then change the AS configuration used by the AS group to the one you created. Your application will be automatically deployed on instances that are automatically added to the AS group. The procedure is as follows:

#. Install the application on the instance you will use to create a private image, and configure the application to automatically start at boot.

#. .. _as_faq_0011__li735592116215:

   Create a private image using the instance. For details, see *Image Management Service User Guide*.

#. .. _as_faq_0011__li6411253193514:

   Create an AS configuration. For details, :ref:`Creating an AS Configuration from a New Specifications Template <as_02_0103>`. During the creation, select the private image created in :ref:`2 <as_faq_0011__li735592116215>`.

#. Go to the page that shows the details about your AS group.

#. Click **Change Configuration** to the right of **Configuration Name**. In the displayed dialog box, select the AS configuration created in :ref:`3 <as_faq_0011__li6411253193514>` and click **OK**.

   After new instances are added to the AS group in the next scaling action, you can check whether your application has been installed on the instances. If you encounter any problems, contact technical support.
