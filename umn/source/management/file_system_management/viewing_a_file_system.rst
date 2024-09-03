:original_name: en-us_topic_0000001476461694.html

.. _en-us_topic_0000001476461694:

Viewing a File System
=====================

You can search for a file system by name keyword or other properties, and view the file system basic information.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, view the file systems you have created. :ref:`Table 1 <en-us_topic_0000001476461694__table37365828114557>` describes the file system parameters.

   .. _en-us_topic_0000001476461694__table37365828114557:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================+
      | Name                              | Name of the file system, for example, **sfs-name-001**                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Redundancy Policy            | Only **Multi-AZ** is supported currently.                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | Availability zone where the file system is located                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Possible values are **Available**, **Unavailable**, **Frozen**, **Creating**, **Deleting**, **Deletion error**, **Creation failed**, **Expanding**, **Expansion error**, **Capacity reducing**, **Capacity reduction error**, and **Capacity reduction failed**. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol Type                     | File system protocol, which is **NFS**                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Used Capacity (GB)                | File system space already used for data storage                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                  |
      |                                   |    This information is refreshed every 15 minutes.                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Maximum Capacity (GB)             | Maximum capacity of the file system                                                                                                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Encrypted                         | Encryption status of the file system. The value can be **Yes** or **No**.                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mount Point                       | File system mount point, which is in the format of *File system domain name*\ **:/**\ *Path* or *File system IP address*\ **:/**                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                  |
      |                                   |    If the mount point is too long to display completely, adjust the column width.                                                                                                                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | For an SFS Capacity-Oriented file system, operations include resizing, deletion, and monitoring metric viewing.                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                  |
      |                                   | For an SFS Turbo file system, operations include capacity expansion, deletion, and monitoring metric viewing.                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click the name of a file system to view detailed information about the file system.


   .. figure:: /_static/images/en-us_image_0000001567316353.png
      :alt: **Figure 1** SFS Capacity-Oriented file system details

      **Figure 1** SFS Capacity-Oriented file system details


   .. figure:: /_static/images/en-us_image_0000001943263244.png
      :alt: **Figure 2** SFS Turbo file system details

      **Figure 2** SFS Turbo file system details

#. (Optional) Search for file systems by file system name keyword, key ID, or file system status.

   You can search for SFS Capacity-Oriented file systems by tag in the upper right area above the file system list.

   -  On the displayed **Search by Tag** tab page, enter a tag key and a tag value (must be among existing keys and values) and click **Search**.
   -  You can use more than one tag for a combination search. Each time after a key and a value are entered, click |image1|. The added search criteria are displayed under the text boxes. When more than one tag is added, they will be applied together for a combination search. A maximum of 20 tags can be added at a time.
   -  You can click **Reset** under the search criteria to reset.

.. |image1| image:: /_static/images/en-us_image_0000001516236408.png
