:original_name: sfs_01_0039.html

.. _sfs_01_0039:

File System Resizing
====================

Scenarios
---------

You can expand or shrink the capacity of a file system when needed.

Limitations and Constraints
---------------------------

The capacity of an SFS Turbo file system can be expanded but cannot be reduced.

SFS Capacity-Oriented file systems support resizing, which does not affect services.

SFS Turbo file systems support online capacity expansion, during which mounting a file system may fail and the connection being used for mounting will experience about a 30-second (max. 3 minutes) I/O latency. You are advised to expand capacity during off-peak hours.

Rules for Resizing
------------------

The rules for resizing an SFS Capacity-Oriented file system are as follows:

-  Expanding a file system

   Total capacity of a file system after expansion <= (Capacity quota of the cloud account - Total capacity of all the other file systems owned by the cloud account)

   For example, cloud account A has a quota of 500 TB. This account has already created three file systems: SFS1 (350 TB), SFS2 (50 TB), and SFS3 (70 TB). If this account needs to expand SFS2, the new capacity of SFS2 cannot be greater than 80 TB. Otherwise, the system will display a message indicating an insufficient quota and the expansion operation will fail.

-  Shrinking a file system

   -  When a shrink error or failure occurs on a file system, it takes approximately five minutes for the file system to restore to the available state.

   -  After a shrink operation fails, you can try shrinking the file system capacity again, but you cannot expand it.

   -  Total capacity of a file system after shrinking >= Used capacity of the file system

      For example, cloud account B has created a file system, SFS1. The total capacity and used capacity of SFS1 are 50 TB and 10 TB respectively. When shrinking SFS1, the user cannot set a new capacity smaller than 10 TB.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, click **Resize** or **Expand Capacity** in the row of the desired file system, as shown in :ref:`Figure 1 <sfs_01_0039__fig50999458171929>`.

   .. _sfs_01_0039__fig50999458171929:

   .. figure:: /_static/images/en-us_image_0000001567196525.png
      :alt: **Figure 1** Resizing an SFS Capacity-Oriented file system

      **Figure 1** Resizing an SFS Capacity-Oriented file system


   .. figure:: /_static/images/en-us_image_0000001970502117.png
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

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================+
      | Current Capacity                  | Current storage capacity of the file system                                                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | New Capacity                      | New storage capacity of the file system                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | Value constraints:                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | -  For a Standard, Standard - Enhanced, Performance, or Performance - Enhanced file system, the expansion increment is 100 GB. A Standard or Performance file system can be expanded to up to 32 TB. A Standard - Enhanced or Performance - Enhanced file system can be expanded to up to 320 TB. |
      |                                   | -  For a 20 MB/s/TiB, 40 MB/s/TiB, 125 MB/s/TiB, or 250 MB/s/TiB file system, the expansion increment is 1.2 TB, and a file system can be expanded to up to 1 PB. The maximum capacity that can be set cannot exceed 1 PB.                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed dialog box, confirm the information and click **OK**.

#. In the file system list, check the capacity information after resizing.
