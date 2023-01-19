:original_name: sfs_01_0039.html

.. _sfs_01_0039:

File System Resizing
====================

Scenarios
---------

You can expand or shrink the capacity of a file system when needed.

Limitations and Constraints
---------------------------

The capacity of an SFS Turbo file system can be expanded but cannot be shrunk.

SFS Capacity-Oriented file systems support resizing, which does not affect services.

SFS Turbo file systems support capacity expansion. During capacity expansion, file systems will be unavailable for 2 to 3 minutes. You are advised to expand the capacity during off-peak hours.

Rules for Resizing
------------------

The rules for resizing an SFS Capacity-Oriented file system are as follows:

-  Expanding a file system

   Total capacity of a file system after expansion <= (Capacity quota of the cloud account - Total capacity of all the other file systems owned by the cloud account)

   For example, cloud account A has a quota of 500 TB. This account has already created three file systems: SFS1 (350 TB), SFS2 (50 TB), and SFS3 (70 TB). If this account needs to expand SFS2, the new capacity of SFS2 cannot be greater than 80 TB. Otherwise, the system will display a message indicating an insufficient quota and the expansion operation will fail.

-  Shrinking a file system

   -  When a shrink error or failure occurs on a file system, it takes approximately five minutes for the file system to restore to the available state.

   -  After a shrink operation fails, you can only reattempt to shrink the file system storage capacity but cannot expand it directly.

   -  Total capacity of a file system after shrinking >= Used capacity of the file system

      For example, cloud account B has created a file system, SFS1. The total capacity and used capacity of SFS1 are 50 TB and 10 TB respectively. When shrinking SFS1, the user cannot set the new capacity to be smaller than 10 TB.

Procedure
---------

#. Log in to SFS Console.

#. In the file system list, click **Resize** or **Expand Capacity** in the row of the desired file system. The following dialog box is displayed. See :ref:`Figure 1 <sfs_01_0039__fig50999458171929>`.

   .. _sfs_01_0039__fig50999458171929:

   .. figure:: /_static/images/en-us_image_0251359565.png
      :alt: **Figure 1** Resizing a file system

      **Figure 1** Resizing a file system

#. Enter a new maximum capacity of the file system based on service requirements, and click **OK**. :ref:`Table 1 <sfs_01_0039__table1834202713541>` describes the parameters.

   .. _sfs_01_0039__table1834202713541:

   .. table:: **Table 1** Parameter description

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

#. In the dialog box that is displayed, confirm the information and click **OK**.

#. In the file system list, check the capacity information after resizing.
