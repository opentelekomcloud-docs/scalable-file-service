:original_name: sfs_01_0125.html

.. _sfs_01_0125:

Writing to a File System Fails
==============================

Symptom
-------

Data fails to be written to the file system mounted to ECSs running the same type of operating system.

Possible Causes
---------------

The ECS security group configuration is incorrect. The port used to communicate with the file system is not enabled.

Fault Diagnosis
---------------

Check whether the port of the target server is enabled and correctly configure the port on the security group console.

Solution
--------

#. Log in to the ECS console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner and select your desired region and project.
   c. Under **Compute**, choose **Elastic Cloud Server**.

#. In the navigation pane on the left, choose **Elastic Cloud Server**. On the page displayed, select the target server. Go to the server details page.

#. Click the **Security Groups** tab and select the target security group. Click **Manage Rule** to go to the security group console.

#. On the displayed page, click the **Inbound Rules** tab and click **Add Rule**. The **Add Inbound Rule** page is displayed. Add rules as follows:

   After an SFS Turbo file system is created, the system automatically enables the security group port required by the NFS protocol. This ensures that the SFS Turbo file system can be accessed by your servers and prevents file system mounting failures. The inbound ports required by the NFS protocol are ports 111, 2049, 2051, 2052, and 20048. If you need to change the enabled ports, go to the VPC console, choose **Access Control** > **Security Groups**, locate the target security group, and change the ports.

   You are advised to use an independent security group for an SFS Turbo file system to isolate it from service nodes.

   You need to add inbound and outbound rules for the security group of an SFS Capacity-Oriented file system. For details, see section "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*. In an SFS Capacity-Oriented file system, the inbound ports required by the NFS protocol are ports 111, 2049, 2051, and 2052. The inbound port required by the DNS server is port 53.

#. Click **OK**. Access the file system again for verification.

.. |image1| image:: /_static/images/en-us_image_0159365094.png
