:original_name: sfs_02_0053.html

.. _sfs_02_0053:

Querying Details About All File Systems
=======================================

Function
--------

This API is used to query details about all SFS Turbo file systems.

URI
---

-  URI format

   GET /v1/{project_id}/sfs-turbo/shares/detail?limit={limit}&offset={offset}

-  Parameter description

   +-----------------+----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory            | Type            | Description                                                                                                              |
   +=================+======================+=================+==========================================================================================================================+
   | project_id      | Yes                  | String          | Specifies the project ID. For details about how to obtain the project ID, see :ref:`API Usage Guidelines <sfs_02_0001>`. |
   +-----------------+----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | limit           | No (query parameter) | Int             | Specifies the number of returned file systems.                                                                           |
   |                 |                      |                 |                                                                                                                          |
   |                 |                      |                 | This parameter takes effect when both **limit** and **offset** are used.                                                 |
   +-----------------+----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | offset          | No (query parameter) | Int             | Specifies the offset of the number of queried file systems.                                                              |
   |                 |                      |                 |                                                                                                                          |
   |                 |                      |                 | This parameter takes effect when both **limit** and **offset** are used.                                                 |
   +-----------------+----------------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example request

   None

Response
--------

-  Parameter description

   +-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                                              |
   +===========+==================+==========================================================================================================================================+
   | shares    | Array of objects | Specifies the list of SFS Turbo file systems. For details, see the :ref:`description of the share field <sfs_02_0053__table1232551195>`. |
   +-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | count     | Int              | Specifies the number of SFS Turbo file systems.                                                                                          |
   +-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of the **share** field

   .. _sfs_02_0053__table1232551195:

   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type   | Description                                                                                                                                                  |
   +===================+========+==============================================================================================================================================================+
   | id                | String | Specifies the ID of the SFS Turbo file system.                                                                                                               |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name              | String | Specifies the name of the SFS Turbo file system.                                                                                                             |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status            | String | Specifies the status of the SFS Turbo file system. For details, see :ref:`SFS Turbo File System Statuses <sfs_02_0085>`.                                     |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sub_status        | String | Specifies the sub-status of the SFS Turbo file system. For details, see :ref:`SFS Turbo File System Substatuses <sfs_02_0086>`.                              |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version           | String | Specifies the version ID of the SFS Turbo file system.                                                                                                       |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at        | String | Specifies the creation time. UTC time, for example: 2018-11-19T04:02:03                                                                                      |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | export_location   | String | Specifies the mount point of the SFS Turbo file system.                                                                                                      |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action_progress   | Object | Specifies the creation progress of the SFS Turbo file system. For details, see :ref:`Description of field action_progress <sfs_02_0053__table117821254414>`. |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_type        | String | Specifies the type of the SFS Turbo file system. The value can be **STANDARD** or **PERFORMANCE**.                                                           |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | region            | String | Specifies the region of the SFS Turbo file system.                                                                                                           |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone | String | Specifies the code of the AZ where the SFS Turbo file system is located.                                                                                     |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | az_name           | String | Specifies the name of the AZ where the SFS Turbo file system is located.                                                                                     |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id            | String | Specifies the VPC ID specified by the user.                                                                                                                  |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id         | String | Specifies the network ID of the subnet specified by the user.                                                                                                |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | String | Specifies the ID of a security group specified by the user.                                                                                                  |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | crypt_key_id      | String | Specifies the ID of the encryption key specified by the user. This parameter is not returned for non-encrypted disks.                                        |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size              | String | Specifies the total capacity of the SFS Turbo file system in the unit of GB.                                                                                 |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pay_model         | String | Billing mode of the SFS Turbo file system.                                                                                                                   |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | avail_capacity    | String | Specifies the available capacity of the SFS Turbo file system in the unit of GB.                                                                             |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_proto       | String | Specifies the protocol type of the SFS Turbo file system. The current value is **NFS**.                                                                      |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expand_type       | String | For an enhanced file system, **bandwidth** is returned for this field. Otherwise, **bandwidth** is not returned.                                             |
   +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of field **action_progress**

.. _sfs_02_0053__table117821254414:

========= ====== ============================================
Parameter Type   Description
========= ====== ============================================
CREATING  String Specifies the file system creation progress.
========= ====== ============================================

-  Example response

   .. code-block::

      {
          "shares": [
              {
                  "id": "8fba8253-c914-439d-ae8b-d5c89d0bf5e8",
                  "name": "sfs-turbo-8468",
                  "status": "200",
                  "version": "1.0.0",
                  "region": "north-1",
                  "created_at": "2018-11-19T04:02:03",
                  "export_location": "192.168.0.90:/",
                  "action_progress": {},
                  "share_type": "STANDARD",
                  "sub_status": "230",
                  "availability_zone": "az1.dc1",
                  "az_name": "az1",
                  "vpc_id": "b24e39e1-bc0c-475b-ae0c-aef9cf240af3",
                  "subnet_id": "86fc01ea-8ec8-409d-ba7a-e0ea16d4fd97",
                  "security_group_id": "50586458-aec9-442c-bb13-e08ddc6f1b7a",
                  "size": "500.00",
                  "pay_model": "0",
                  "avail_capacity": "500.00",
                  "share_proto": "NFS"
              },
              {
                  "id": "65f2d30b-7b4e-4786-9608-4324faef6646",
                  "name": "sfs-turbo-df12",
                  "status": "200",
                  "version": "1.0.0",
                  "actions": [],
                  "region": "north-1",
                  "created_at": "2018-11-15T02:32:10",
                  "export_location": "192.168.0.197:/",
                  "action_progress": {},
                  "share_type": "STANDARD",
                  "availability_zone": "az1.dc1",
                  "az_name": "az1",
                  "vpc_id": "b24e39e1-bc0c-475b-ae0c-aef9cf240af3",
                  "subnet_id": "86fc01ea-8ec8-409d-ba7a-e0ea16d4fd97",
                  "security_group_id": "50586458-aec9-442c-bb13-e08ddc6f1b7a",
                  "size": "500.00",
                  "pay_model": "0",
                  "avail_capacity": "500.00",
                  "share_proto": "NFS"
              }
          ]
          "count": 2
      }

Status Codes
------------

-  Normal

200

-  Abnormal

For details, see :ref:`Status Codes <sfs_02_0089>`.
