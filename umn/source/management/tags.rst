:original_name: sfs_01_0043.html

.. _sfs_01_0043:

Tags
====

This section describes how to add tags to existing file systems. You can also add tags when creating file systems. For details, see section :ref:`Create a File System <en-us_topic_0034428727>`.

Tags are used to identify and classify file systems.

-  Tags are composed of key-value pairs.

   -  A tag key can contain a maximum of 36 characters and cannot be left blank. It must start with a letter and can only contain letters, digits, hyphens (-), underscores (_), and at signs (@).
   -  A tag value can contain a maximum of 43 characters and can be an empty string. It must start with a letter and can only contain letters, digits, hyphens (-), underscores (_), and at signs (@).

-  You can add a maximum of 20 tags to a file system.
-  The tag keys of the same file system must be unique.
-  Once created, the tag keys of the file system cannot be edited. You can only edit the tag values. You can delete tags.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, find the file system to which you want to add tags and click the name of it. The file system details page is displayed, as shown in :ref:`Figure 1 <sfs_01_0043__fig146683492144>`.

   .. _sfs_01_0043__fig146683492144:

   .. figure:: /_static/images/en-us_image_0251361308.png
      :alt: **Figure 1** Managing file system tags

      **Figure 1** Managing file system tags

#. Click the **Tags** tab.

#. On the **Tags** tab page, click **Edit Tag** to open the **Edit Tag** dialog box.

#. Add the key and value of the tag and click **OK**.

   -  **Key**: This parameter is mandatory.
   -  **Value**: This parameter is optional.

   Return to the tag list, and you can see the tags you have just added. You can edit and delete the added tags.
