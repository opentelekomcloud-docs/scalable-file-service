:original_name: sfs_02_0025.html

.. _sfs_02_0025:

Querying Mount Locations of a Shared File System
================================================

Function
--------

This API is used to query mount locations of a shared file system.

.. note::

   This API exists only when **X-Openstack-Manila-Api-Version** in the request header is greater than or equal to 2.9. The following is an example request sent by the **curl** command: curl -k -i -X GET https://192.168.196.47:8786/v2/13c7ff9a479c4e3599f4331d9e4a1835/shares/2a8c5470-d5d9-4fe1-b9fc-66a15a162e41/export_locations **-H "X-Openstack-Manila-Api-Version: 2.9"** -H "X-Auth-Token: $token" -H "Accept: application/json"

URI
---

-  GET /v2/{project_id}/shares/{share_id}/export_locations
-  Parameter description

   ========== ========= ====== ===========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================================
   share_id   Yes       String Specifies the ID of the shared file system.
   project_id Yes       String Specifies the project ID of the operator.
   ========== ========= ====== ===========================================

Request
-------

-  Parameter description

   None

-  Example request

   None

Response
--------

-  Parameter description

   +------------------+------------------+--------------------------------------------+
   | Parameter        | Type             | Description                                |
   +==================+==================+============================================+
   | export_locations | Array of strings | Specifies the **export_location** objects. |
   +------------------+------------------+--------------------------------------------+

-  Description of field **export_location**

   +-------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type    | Description                                                                                                                                                                                                 |
   +===================+=========+=============================================================================================================================================================================================================+
   | id                | String  | Specifies the ID of the mount location of the shared file system.                                                                                                                                           |
   +-------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_instance_id | String  | Specifies the ID of the shared file system.                                                                                                                                                                 |
   +-------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | path              | String  | Specifies the path that will be used when the shared file system is mounted.                                                                                                                                |
   +-------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_admin_only     | Boolean | Specifies whether the shared file system is only visible to administrators and its owner. Possible values are **true** (only visible to administrators and its owner) and **false** (visible to all users). |
   +-------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | preferred         | Boolean | Identifies which mount locations are most efficient and are used preferentially when multiple mount locations exist.                                                                                        |
   +-------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   NFS file system:

   .. code-block::

      {
        "export_locations": [
          {
            "path": "NFS:sfs-nas1.dong.com:/share-236b936a",
            "id": "b03d2aac-aeed-409a-af07-5d1b9024241c",
            "preferred": false
          }
        ]
      }

Status Codes
------------

-  Normal

   200

-  Abnormal

   +------------------+--------------------------------------------------------------------------+
   | Status Code      | Description                                                              |
   +==================+==========================================================================+
   | 400 Bad Request  | The server failed to process the request.                                |
   +------------------+--------------------------------------------------------------------------+
   | 401 Unauthorized | You must enter a username and the password to access the requested page. |
   +------------------+--------------------------------------------------------------------------+
   | 403 Forbidden    | Access to the requested page is forbidden.                               |
   +------------------+--------------------------------------------------------------------------+
   | 404 Not Found    | The requested page was not found.                                        |
   +------------------+--------------------------------------------------------------------------+
