:original_name: en-us_topic_0000001567076569.html

.. _en-us_topic_0000001567076569:

Viewing a File System
=====================

You can search for file systems by file system name keyword or file system status, and view their basic information.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, view the file systems you have created. :ref:`Table 1 <en-us_topic_0000001567076569__table37365828114557>` describes the file system parameters.

   .. _en-us_topic_0000001567076569__table37365828114557:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================+
      | Name                              | Name of the file system, for example, **sfs-name-001**                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | Availability zone where the file system is located                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Possible values are **Available**, **Unavailable**, **Frozen**, **Creating**, **Deleting**, **Deletion error**, **Creation failed**, **Expanding**, **Expansion error**, **Capacity reducing**, **Capacity reduction error**, and **Capacity reduction failed**. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol Type                     | File system protocol, which is **NFS**                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Available Capacity (GB)           | Remaining file system space available to data storage                                                                                                                                                                                                            |
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

#. Click the name of a file system to view detailed information about the file system. See :ref:`Figure 1 <en-us_topic_0000001567076569__fig964613241271>`.

   .. _en-us_topic_0000001567076569__fig964613241271:

   .. figure:: /_static/images/en-us_image_0000001567316353.png
      :alt: **Figure 1** File system information

      **Figure 1** File system information

#. (Optional) Search for file systems by file system name keyword, key ID, or file system status.

   In the upper right corner of the page, click **Search by Tag** to query file systems by tag.

   -  On the displayed **Search by Tag** tab page, enter a tag key and a tag value (must be among existing keys and values) and click **Search**.
   -  You can use more than one tag for a combination search. Each time after a key and a value are entered, click |image1|. The added search criteria are displayed under the text boxes. When more than one tag is added, they will be applied together for a combination search. A maximum of 10 tags can be added at a time.
   -  You can click **Reset** under the search criteria to reset.

.. |image1| image:: /_static/images/en-us_image_0000001516236408.png
