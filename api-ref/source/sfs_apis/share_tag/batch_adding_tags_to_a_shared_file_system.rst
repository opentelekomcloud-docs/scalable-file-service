:original_name: sfs_02_0041.html

.. _sfs_02_0041:

Batch Adding Tags to a Shared File System
=========================================

Function
--------

This API is used to batch add tags to a specified shared file system.

A shared file system can have a maximum of 10 tags.

The keys of multiple tags added to a shared file system must be unique.

This API is idempotent. If the key to be added has already been added to the shared file system, the tag is updated.

URI
---

-  POST /v2/{project_id}/sfs/{share_id}/tags/action
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

   +-----------------+-----------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                   | Description                                                                                                                                            |
   +=================+=================+========================+========================================================================================================================================================+
   | action          | Yes             | String                 | Specifies the operation identifier. Possible values are **create** and **delete**. Use **create** to batch add tags to a specified shared file system. |
   +-----------------+-----------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of resource_tags | Specifies the tag list.                                                                                                                                |
   |                 |                 |                        |                                                                                                                                                        |
   |                 |                 |                        | This parameter is mandatory when the tenant permission is used. For the op_service permission, choose either this field or **sys_tags**.               |
   +-----------------+-----------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags        | No              | Array of resource_tags | Specifies the system tag list.                                                                                                                         |
   |                 |                 |                        |                                                                                                                                                        |
   |                 |                 |                        | This field is available only to the op_service permission. Choose either this field or **tags**.                                                       |
   |                 |                 |                        |                                                                                                                                                        |
   |                 |                 |                        | Currently, TMS invokes only one resource_tag structure. The key is fixed as **\_sys_enterprise_project_id**.                                           |
   |                 |                 |                        |                                                                                                                                                        |
   |                 |                 |                        | The value is **ID** or **0**.                                                                                                                          |
   +-----------------+-----------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of field **resource_tag**

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                          |
   +===========+===========+========+======================================================================================================================================================================================+
   | key       | Yes       | String | Specifies the key of the tag. The value can contain a maximum of 36 characters. The key cannot be left blank and can only contain letters, digits, hyphens (-), and underscores (_). |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | Yes       | String | Specifies the value of the tag. The value contains a maximum of 43 characters and can be an empty string. It can only contain letters, digits, hyphens (-), and underscores (_).     |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "action": "create",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value2"
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
