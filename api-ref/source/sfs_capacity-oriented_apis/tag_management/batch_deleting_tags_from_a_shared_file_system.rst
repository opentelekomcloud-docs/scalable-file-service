:original_name: sfs_02_0042.html

.. _sfs_02_0042:

Batch Deleting Tags from a Shared File System
=============================================

Function
--------

This API is used to batch delete tags from a specified shared file system.

This API is idempotent. If the tags to be deleted do not exist on the shared file system, the deletion is regarded as successful by default.

URI
---

-  POST /v2/{project_id}/sfs/{share_id}/tags/action
-  Parameter description

   ========== ========= ====== ===========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================================
   project_id Yes       String Specifies the project ID of the operator.
   share_id   Yes       String Specifies the ID of the shared file system.
   ========== ========= ====== ===========================================

Request
-------

-  Parameter description

   +-----------+-----------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                   | Description                                                                                                                                                 |
   +===========+===========+========================+=============================================================================================================================================================+
   | action    | Yes       | String                 | Specifies the operation identifier. Possible values are **create** and **delete**. Use **delete** to batch delete tags from a specified shared file system. |
   +-----------+-----------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags      | Yes       | Array of resource_tags | Specifies the tag list.                                                                                                                                     |
   +-----------+-----------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of field **resource_tag**

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================================================================+
   | key             | Yes             | String          | Specifies the tag key.                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                             |
   |                 |                 |                 | The value can contain a maximum of 36 characters. This parameter cannot be left blank.                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Specifies the tag value.                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                             |
   |                 |                 |                 | The value contains a maximum of 43 characters and can be an empty string. If the value is not an empty string, the tag is located and deleted based on the key and value. If the value is an empty string, the tag is located and deleted based on the key. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "action": "delete",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2"
              },
              {
                  "key": "key3",
                  "value": ""
              }
          ]
      }

Response
--------

-  Parameter description

   None

-  Example response

   None

Status Codes
------------

-  Normal

   204

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
