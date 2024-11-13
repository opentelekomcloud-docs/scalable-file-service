:original_name: sfs_01_0134.html

.. _sfs_01_0134:

Configure a VPC Endpoint
========================

Context
-------

VPC Endpoint provides reliable channels to connect VPCs to general purpose file systems. By configuring VPC endpoints, compute resources in VPCs can access general purpose file systems.

Before mounting a general purpose file system to a compute resource, you need to create a VPC endpoint in the region where the compute resource belongs.

VPC endpoints are not required for SFS Capacity-Oriented and SFS Turbo file systems.

Prerequisites
-------------

#. Before creating a general purpose file system, ensure that a VPC is available.

   If no VPC is available, create one by referring to section "Creating a VPC" in the *Virtual Private Cloud User Guide*.

#. Before creating a general purpose file system, ensure that ECSs are available and in the created VPC.

   If no ECS is available, create ECSs by referring to "Creating an ECS" in the *Elastic Cloud Server User Guide*.

Procedure
---------

#. Log in to the console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner and select your desired region and project.
   c. Choose **Networking** > **VPC Endpoint** > **VPC Endpoints**.

#. On the **VPC Endpoints** page, click **Create VPC Endpoint**.

   The **Create VPC Endpoint** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001310873016.png
      :alt: **Figure 1** Create VPC Endpoint

      **Figure 1** Create VPC Endpoint

#. Set the parameters as prompted.

   .. table:: **Table 1** Parameters for purchasing an endpoint

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================+
      | Region                            | Region where the VPC endpoint is located. Ensure that this region is the same as the one where the planned general purpose file system resides.                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Service Category                  | Select **Find a service by name**.                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | Enter **com.t-systems.otc.eu-de.lz02.obsv2.ipv4**.                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | After entering the service name, click **Verify**.                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | If **Service name found** is displayed, proceed with subsequent steps.                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | If **Service name not found** is displayed, check whether the entered service name is correct. If the problem persists, contact the website administrator.                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPC                               | VPC where the planned general purpose file system and ECSs reside.                                                                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | Optional                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | VPC endpoint tags. Each tag consists of a key and a value.                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | Tag keys and values must meet the requirements listed in :ref:`Table 2 <sfs_01_0134__table191162312815>`.                                                                                                                   |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                             |
      |                                   |    -  If a predefined tag has been created in TMS, you can select the corresponding tag key and value. For details about predefined tags, see section "Predefined Tag Overview" in the *Tag Management Service User Guide*. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   :ref:`Table 2 <sfs_01_0134__table191162312815>` describes the tag parameters.

   .. _sfs_01_0134__table191162312815:

   .. table:: **Table 2** Tag parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                               | Example Value         |
      +=======================+===========================================================================================================+=======================+
      | Tag key               | Each tag has a unique key. You can customize the key or select the key of an existing tag created in TMS. | Key_0001              |
      |                       |                                                                                                           |                       |
      |                       | A tag key:                                                                                                |                       |
      |                       |                                                                                                           |                       |
      |                       | -  Can contain 1 to 36 Unicode characters.                                                                |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), and underscores (_).                                    |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag value             | A tag value can be repetitive or left blank.                                                              | Value_0001            |
      |                       |                                                                                                           |                       |
      |                       | A tag value:                                                                                              |                       |
      |                       |                                                                                                           |                       |
      |                       | -  Can contain 0 to 43 Unicode characters.                                                                |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), and underscores (_).                                    |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Next**.

   -  If you do not need to modify the specifications, click **Submit**.
   -  If you need to modify the specifications, click **Previous**, modify the parameters as needed, and then click **Submit**.

#. Go back to the VPC endpoint list and check whether the status of the VPC endpoint changes to **Accepted**. If so, the VPC endpoint has been connected to the VPC endpoint service.

.. |image1| image:: /_static/images/en-us_image_0159365094.png
