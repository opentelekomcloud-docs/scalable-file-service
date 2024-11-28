:original_name: sfs_01_0039.html

.. _sfs_01_0039:

File System Resizing
====================

Scenarios
---------

You can expand or shrink the capacity of a file system when needed.

Constraints
-----------

SFS Turbo file systems can only have their capacities expanded, not reduced. And only **In-use** file systems can be expanded.

SFS Capacity-Oriented file systems support resizing, during which services are not affected. Only **In-use** file systems can be expanded.

SFS Turbo file systems support online capacity expansion, during which mounting a file system may fail and the connection being used for mounting will experience about a 30-second (max. 3 minutes) I/O delay. So you are advised to expand capacity during off-peak hours. Note that only **In-use** file systems can be expanded.

General purpose file systems have no capacity limit and do not support resizing.

Precautions
-----------

The rules for resizing an SFS Capacity-Oriented file system are as follows:

-  Expanding a file system

   Total capacity of a file system after expansion <= (Capacity quota of the cloud account - Total capacity of all the other file systems owned by the cloud account)

   For example, a cloud account has a quota of 500 TB. This account has already created three file systems: SFS1 (350 TB), SFS2 (50 TB), and SFS3 (70 TB). If this account needs to expand SFS2, the new capacity of SFS2 cannot be greater than 80 TB. Otherwise, the system will display a message indicating an insufficient quota and the expansion operation will fail.

-  Shrinking a file system

   -  When a shrink error or failure occurs on a file system, it takes approximately five minutes for the file system to restore to the available state.

   -  After a shrink operation fails, you can only reattempt to shrink the file system storage capacity but cannot expand it directly.

   -  Total capacity of a file system after shrinking >= Used capacity of the file system

      For example, a cloud account has created a file system, SFS1. The total capacity and used capacity of SFS1 are 50 TB and 10 TB respectively. When shrinking SFS1, the user cannot set a new capacity smaller than 10 TB.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, click **Resize** or **Expand Capacity** in the row of the desired file system. The following dialog box is displayed


   .. figure:: /_static/images/en-us_image_0251359565.png
      :alt: **Figure 1** Resizing an SFS Capacity-Oriented file system

      **Figure 1** Resizing an SFS Capacity-Oriented file system


   .. figure:: /_static/images/en-us_image_0000001921925536.png
      :alt: **Figure 2** Expanding an SFS Turbo file system

      **Figure 2** Expanding an SFS Turbo file system

#. Enter a new capacity and click **OK**. The following tables describe the parameters.

   .. table:: **Table 1** SFS Capacity-Oriented file system resizing parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                               |
      +===================================+===========================================================================================================================+
      | Used Capacity (GB)                | Used capacity of the current file system                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Maximum Capacity (GB)             | Maximum capacity of the current file system                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | New Maximum Capacity (GB)         | Target maximum capacity of the file system after expanding or shrinking The value ranges from **1 GB** to **512,000 GB**. |
      |                                   |                                                                                                                           |
      |                                   | .. note::                                                                                                                 |
      |                                   |                                                                                                                           |
      |                                   |    The new maximum capacity cannot be smaller than the used capacity.                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** SFS Turbo file system capacity expansion parameters

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================================================================================+
      | Current Capacity                  | Current storage capacity of the file system                                                                                                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | New Capacity                      | New storage capacity of the file system                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                           |
      |                                   | Value constraints:                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                           |
      |                                   | -  For a Standard, Standard-Enhanced, Performance, or Performance-Enhanced file system, the minimum expansion increment is 100 GB. A Standard or Performance file system can be expanded to up to 32 TB, and a Standard - Enhanced or Performance - Enhanced file system can be expanded to up to 320 TB. |
      |                                   | -  For a 20 MB/s/TiB, 40 MB/s/TiB, 125 MB/s/TiB, or 250 MB/s/TiB file system, the expansion increment is 1.2 TB, and a file system can be expanded to up to 1 PB.                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed dialog box, confirm the information and click **OK**.

#. In the file system list, check the capacity information after resizing.
