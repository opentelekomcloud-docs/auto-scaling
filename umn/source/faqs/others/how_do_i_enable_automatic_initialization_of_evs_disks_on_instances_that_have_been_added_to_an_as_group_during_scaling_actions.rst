:original_name: as_faq_0008.html

.. _as_faq_0008:

How Do I Enable Automatic Initialization of EVS Disks on Instances that Have Been Added to an AS Group During Scaling Actions?
==============================================================================================================================

Scenarios
---------

After an ECS instance is created, you need to manually initialize EVS disks attached to the instance before using them. If multiple instances are added to the AS group, you must initialize the EVS disks on each instance, which takes a while.

This section describes how to configure a script to enable automatic initialization of EVS disks, including disk partitioning and attachment of specified directories. The script can only be used to initialize one EVS disk.

This section uses CentOS 6.5 as an example. For how to configure automatic initialization of EVS disks on other OSs, see the relevant OS documentation.

Procedure
---------

#. Log in to the instance as user **root**.

#. Run a command to switch to the directory where the script will be stored:

   **cd /**\ *script directory*

   For example:

   **cd /home**

#. Run the following command to create the script:

   **vi** *script name*

   For example:

   **vi fdisk_mount.sh**

#. Press **i** to enter editing mode.

   The following script is used as an example to show how to implement automatic initialization of one data disk:

   .. code-block::

      #!/bin/bash
      bash_scripts_name=fdisk_mount.sh
      ini_path=/home/fdisk.ini
      disk=
      size=
      mount=
      partition=

      function get_disk_from_ini()
      {
      disk=`cat $ini_path|grep disk| awk -F '=' '{print $2}'`
      if [ $disk = "" ]
      then
          echo "disk is null in file,exit"
          exit
      fi
      result=`fdisk -l $disk | grep $disk`
      if [ $result = 1 ]
      then
          echo "disk path does not exist in linux,exit"
          exit
      fi

      }

      function get_size()
      {
      size=`cat $ini_path| grep size|awk -F '=' '{print $2}'`
      if [ $size = "" ]
      then
          echo "size is null,exit"
          exit
      fi
      }

      function make_fs_mount()
      {
      mkfs.ext4 -T largefile $partition
      if [ $? -ne 0 ]
      then
          echo "mkfs disk failed,exit"
          exit
      fi

      dir=`cat $ini_path|grep mount |awk -F '=' '{print $2}'`
      if [ $dir = "" ]
      then
          echo "mount dir is null in file,exit"
          exit
      fi

      if [ ! -d $dir ]
      then
          mkdir -p $dir
      fi

      mount $partition $dir
      if [ $? -ne 0 ]
      then
          echo "mount disk failed,exit"
          exit
      fi

      echo "$partition $dir ext3 defaults 0 0" >> /etc/fstab
      }

      function remove_rc()
      {
      cat /etc/rc.local | grep $bash_scripts_name
      if [ $? ne 0 ]
      then
          sed -i '/'$bash_scripts_name'/d' /etc/rc.local
      fi
      }

      ################## start #######################
      ##1. Check whether the configuration file exists.
      if [ ! -f $ini_path ]
      then
          echo "ini file not exist,exit"
          exit
      fi

      ##2. Obtain the device path for the specified disk from the configuration file.
      get_disk_from_ini

      ##3. Obtain the size of the size partition from the configuration file.
      get_size

      ##4. Partition the disk.
      fdisk $disk  <<EOF
      n
      p
      1
      1
      $size
      w
      EOF
      partition=`fdisk -l $disk 2>/dev/null| grep "^/dev/[xsh].*d" | awk '{print $1}'`

      ##5. Format the partition and attach the partition to the specified directory.
      make_fs_mount

      ##6. Change startup items to prevent re-execution of the scripts.
      remove_rc

      echo 'SUCESS'

#. Press **Esc**, enter **:wq**, and press **Enter** to save the changes and exit.

#. Run the following command to create the configuration file:

   **vi fdisk.ini**

#. Press **i** to enter editing mode.

   The drive letter, size, and mount directory of the EVS disk are configured in the configuration file. You can change the settings based on the following displayed information.

   .. code-block::

      disk=/dev/xdev
      size=+100G
      mount=/opt/test

#. Press **Esc**, enter **:wq**, and press **Enter** to save the changes and exit.

#. Run the following command to open configuration file **rc.local**:

   **vi /etc/rc.local**

#. Press **i** to add the following content to **rc.local**:

   **/home/fdisk_mount.sh**

   After **rc.local** is configured, the EVS disk initialization script will be automatically executed when the ECS starts.

#. Press **Esc**, enter **:wq**, and press **Enter** to save the changes and exit.

#. Create a private image using an ECS.

#. Create an AS configuration.

   When you specify the AS configuration information, select the private image created in the preceding step and select an EVS disk.

#. Create an AS group.

   When you configure the AS group, select the AS configuration created in the preceding step.

   After the AS group is created, EVS disks of new instances added to this AS group in scaling actions will be automatically initialized.
