:original_name: sfs_02_0097.html

.. _sfs_02_0097:

Changing a Security Group
=========================

Function
--------

This API is used to change the security group bound to an SFS Turbo file system. Security group change is an asynchronous task. You can determine whether the security group status is changed based on the **sub_status** field returned in :ref:`Querying Details About a Single File System <sfs_02_0054>`. If the **sub_status** field is **232**, the security group has been successfully modified.

URI
---

-  URI format

   POST /v1/{project_id}/sfs-turbo/shares/{share_id}/action

-  Parameter description

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                              |
   +============+===========+========+==========================================================================================================================+
   | project_id | Yes       | String | Specifies the project ID. For details about how to obtain the project ID, see :ref:`API Usage Guidelines <sfs_02_0001>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | share_id   | Yes       | String | Specifies the ID of the SFS Turbo file system.                                                                           |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type   | Description                                                                                                                                                 |
   +=======================+===========+========+=============================================================================================================================================================+
   | change_security_group | Yes       | Object | Specifies the **change_security_group** object. For details, see the :ref:`change_security_group parameter description <sfs_02_0097__table19964132917205>`. |
   +-----------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  change_security_group parameter description

   .. _sfs_02_0097__table19964132917205:

   +-------------------+-----------+--------+--------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                            |
   +===================+===========+========+========================================================+
   | security_group_id | Yes       | String | Specifies the ID of the security group to be modified. |
   +-------------------+-----------+--------+--------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "change_security_group": {
             "security_group_id": "26f6b565-240e-43c3-8867-03f0bd975433"
          }
      }

Response
--------

-  Parameter description

   ========= ====== ==============================================
   Parameter Type   Description
   ========= ====== ==============================================
   id        String Specifies the ID of the SFS Turbo file system.
   ========= ====== ==============================================

-  Example response

   .. code-block::

      {
          "id": "67d4bd5e-7b2f-4c24-9a0b-c0038940c6f8"
      }

Status Codes
------------

-  Normal

202

-  Abnormal

For details, see :ref:`Status Codes <sfs_02_0089>`.
