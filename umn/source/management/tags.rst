:original_name: sfs_01_0043.html

.. _sfs_01_0043:

Tags
====

This section describes how to add tags to existing file systems. You can also add tags when creating file systems. For details, see :ref:`Create a File System <en-us_topic_0034428727>`.

Tags are used to identify and classify file systems.

-  Tags are composed of key-value pairs.

   -  A tag key can contain a maximum of 128 characters and cannot be left blank. For a general purpose file system, a tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but it cannot start or end with a space or start with \_sys_. For an SFS Turbo file system, a tag key can contain only letters, digits, hyphens (-), underscores (_), and at signs (@).
   -  A tag value can contain a maximum of 255 characters and can be an empty string. For a general purpose file system, a tag value can contain letters, digits, spaces, and special characters ``(_.:/=+-@),`` but it cannot start or end with a space. For an SFS Turbo file system, a tag value can contain only letters, digits, hyphens (-), and underscores (_).

-  You can add a maximum of 20 tags to a file system.
-  Tag keys of the same file system must be unique.
-  After adding a tag to a file system, you can edit the tag key and value, or delete the tag.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, find the file system to which you want to add tags and click its name to go to its details page.


   .. figure:: /_static/images/en-us_image_0000002483494348.png
      :alt: **Figure 1** Tags of a general purpose file system

      **Figure 1** Tags of a general purpose file system


   .. figure:: /_static/images/en-us_image_0251361308.png
      :alt: **Figure 2** Tags of an SFS Turbo file system

      **Figure 2** Tags of an SFS Turbo file system

#. Click the **Tags** tab.

#. On the **Tags** tab, click **Edit Tag**.

   The Edit Tag dialog box is displayed.

#. Add the key and value of the tag and click **OK**.

   -  **Key**: This parameter is mandatory.
   -  **Value**: This parameter is optional.

   Return to the tag list, and you can see the tags you have just added. You can edit and delete the added tags.
