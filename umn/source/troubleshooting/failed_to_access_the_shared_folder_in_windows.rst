:original_name: sfs_01_0063.html

.. _sfs_01_0063:

Failed to Access the Shared Folder in Windows
=============================================

Symptom
-------

When you mount a file system to an ECS running Windows, the system displays a message "You cannot access this shared folder because your organization's security policies block unauthenticated guest access. These policies help to protect you PC from unsafe or malicious devices on the network."

Possible Causes
---------------

Guest access to CIFS file systems is blocked or disabled.

Fault Diagnosis
---------------

Solution 1: Manually enable guest access.

Solution 2: Modify the registry to allow guest access (suitable for versions later than Windows Server 2016).

Solution
--------

**Solution 1: Manually enable guest access.**

#. Open **Run** command box, enter **gpedit.msc**, and press **Enter** to start **Local Group Policy Editor**.


   .. figure:: /_static/images/en-us_image_0000001567076805.png
      :alt: **Figure 1** Entering gpedit.msc

      **Figure 1** Entering gpedit.msc

#. On the **Local Group Policy Editor** page, choose **Computer Configuration** > **Administrative Templates**.


   .. figure:: /_static/images/en-us_image_0000001567316461.png
      :alt: **Figure 2** Local Group Policy Editor

      **Figure 2** Local Group Policy Editor

#. Under **Administrative Templates**, choose **Network** > **Lanman Workstation** and find the option of **Enable insecure guest logons**.


   .. figure:: /_static/images/en-us_image_0000001515917384.png
      :alt: **Figure 3** Locating the option

      **Figure 3** Locating the option

#. Double-click **Enable insecure guest logons**. Select **Enabled** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001516076964.png
      :alt: **Figure 4** Enabling insecure guest logons

      **Figure 4** Enabling insecure guest logons

#. After the access is enabled, mount the file system again. If the fault persists, contact technical support.

**Solution 2: Modify the registry to allow guest access (suitable for versions later than Windows Server 2016).**

#. Choose **Start** > **Run** and enter **regedit** to open the registry.

#. Go to the **HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters** directory.


   .. figure:: /_static/images/en-us_image_0000001567396721.png
      :alt: **Figure 5** Entering the registry

      **Figure 5** Entering the registry

#. Right-click **AllowInsecureGuestAuth** and choose **Modify** from the shortcut menu. In the pop-up window, change the value to **1**.


   .. figure:: /_static/images/en-us_image_0000001516236536.png
      :alt: **Figure 6** Changing the value

      **Figure 6** Changing the value
