:original_name: sfs_02_0056.html

.. _sfs_02_0056:

Expanding the Capacity of a File System
=======================================

Function
--------

This API is used to expand the capacity of an SFS Turbo file system. Capacity expansion is an asynchronous operation. You can check whether the expansion is successful by checking field **sub_status** returned by :ref:`Querying Details About a Single File System <sfs_02_0054>`. If the value of the sub-status is **221**, the expansion is successful.

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

   .. _sfs_02_0056__table20355323:

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                              |
   +===========+===========+========+==========================================================================================================================+
   | extend    | Yes       | Object | Specifies the **extend** object. For details, see the :ref:`parameter in the extend field <sfs_02_0056__table20355323>`. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

-  Parameter in the **extend** field

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | new_size        | Yes             | Int             | Specifies the new capacity (GB) of the shared file system. The capacity expansion step is greater than or equal to 100 GB. |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | For a common file system, the value of capacity ranges from 500 to 32768.                                                  |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | For an enhanced file system, the value of capacity ranges from 10240 to 327680.                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "extend": {
             "new_size": 500
          }
      }

Response
--------

-  Parameter description

   ========= ====== ================================================
   Parameter Type   Description
   ========= ====== ================================================
   id        String Specifies the ID of the SFS Turbo file system.
   name      String Specifies the name of the SFS Turbo file system.
   ========= ====== ================================================

-  Example response

   .. code-block::

      {
          "id": "67d4bd5e-7b2f-4c24-9a0b-c0038940c6f8",
          "name": "sfs-turbo-cts"
      }

Status Codes
------------

-  Normal

202

-  Abnormal

For details, see :ref:`Status Codes <sfs_02_0089>`.
