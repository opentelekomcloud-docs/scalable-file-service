:original_name: sfs_02_0039.html

.. _sfs_02_0039:

Querying Tag Information About a Shared File System
===================================================

Function
--------

This API is used to query all tag information about the specified shared file system.

URI
---

-  GET /v2/{project_id}/sfs/{share_id}/tags
-  Parameter description

   ========== ========= ====== =========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================================
   project_id Yes       String Specifies the project ID of the operator.
   share_id   Yes       String Specifies the share ID.
   ========== ========= ====== =========================================

Request
-------

-  Parameter description

   None

-  Example request

   None

Response
--------

-  Parameter description

   +-----------------------+------------------------+---------------------------------------------------------------------------------------------+
   | Parameter             | Type                   | Description                                                                                 |
   +=======================+========================+=============================================================================================+
   | tags                  | Array of resource_tags | Specifies the list of tags.                                                                 |
   +-----------------------+------------------------+---------------------------------------------------------------------------------------------+
   | sys_tags              | Array of resource_tags | Only the op_service permission can obtain this field.                                       |
   |                       |                        |                                                                                             |
   |                       |                        | #. Currently, only one resource_tag structure key is used, **\_sys_enterprise_project_id**. |
   |                       |                        | #. Currently, **key** contains only one value.                                              |
   |                       |                        |                                                                                             |
   |                       |                        | This field cannot be returned in non-op_service scenarios.                                  |
   +-----------------------+------------------------+---------------------------------------------------------------------------------------------+

-  Description of field **resource_tag**

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   key       String Specifies the key of the tag.
   value     String Specifies the value of the tag.
   ========= ====== ===============================

-  Example response

   .. code-block::

      {
             "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": ""
              }
          ]
      }

Status Codes
------------

-  Normal

   200

-  Abnormal

   +---------------------------+----------------------------------------------------------+
   | Status Code               | Description                                              |
   +===========================+==========================================================+
   | 400 Bad Request           | Invalid value.                                           |
   +---------------------------+----------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                   |
   +---------------------------+----------------------------------------------------------+
   | 403 Forbidden             | Access to the requested page is forbidden.               |
   +---------------------------+----------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                    |
   +---------------------------+----------------------------------------------------------+
   | 500 Internal Server Error | The request is not completed because of a service error. |
   +---------------------------+----------------------------------------------------------+
