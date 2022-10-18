:original_name: sfs_02_0052.html

.. _sfs_02_0052:

Deleting a File System
======================

Function
--------

This API is used to delete an SFS Turbo file system.

URI
---

-  URI format

   DELETE /v1/{project_id}/sfs-turbo/shares/{share_id}

-  Parameter description

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                              |
   +============+===========+========+==========================================================================================================================+
   | project_id | Yes       | String | Specifies the project ID. For details about how to obtain the project ID, see :ref:`API Usage Guidelines <sfs_02_0001>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | share_id   | Yes       | String | Specifies the ID of an SFS Turbo file system.                                                                            |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  None

Response
--------

-  None

Status Codes
------------

-  Normal

202

-  Abnormal

For details, see :ref:`Status Codes <sfs_02_0089>`.
