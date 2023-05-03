:original_name: sfs_02_0078.html

.. _sfs_02_0078:

Batch Adding Tags to a File System
==================================

Function
--------

This API is used to batch add tags to an SFS Turbo file system.

A shared file system can have a maximum of 10 tags.

The keys of multiple tags added to a shared file system must be unique.

This API is idempotent. If the key to be added has already been added to the shared file system, the tag is updated.

URI
---

-  POST /v1/{project_id}/sfs-turbo/{share_id}/tags/action
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

   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                         |
   +=================+=================+====================+=====================================================================================================================================================================================================================================+
   | action          | Yes             | String             | Specifies the operation identifier. Possible values are **create** and **delete**. Use **create** to batch add tags to a specified shared file system.                                                                              |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | list<resource_tag> | Specifies the tag list.                                                                                                                                                                                                             |
   |                 |                 |                    |                                                                                                                                                                                                                                     |
   |                 |                 |                    | This parameter is mandatory when the tenant permission is used. For the op_service permission, choose either this field or **sys_tags**. For details, see :ref:`Description of field resource_tag <sfs_02_0078__table69719318161>`. |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags        | No              | List<resource_tag> | Specifies the system tag list.                                                                                                                                                                                                      |
   |                 |                 |                    |                                                                                                                                                                                                                                     |
   |                 |                 |                    | This field is available only to the op_service permission. Choose either this field or **tags**.                                                                                                                                    |
   |                 |                 |                    |                                                                                                                                                                                                                                     |
   |                 |                 |                    | Only one resource_tag structure key, **\_sys_enterprise_project_id**, is used in TMS calls.                                                                                                                                         |
   |                 |                 |                    |                                                                                                                                                                                                                                     |
   |                 |                 |                    | The value is **ID** or **0**. Value **0** indicates the default enterprise project.                                                                                                                                                 |
   |                 |                 |                    |                                                                                                                                                                                                                                     |
   |                 |                 |                    | For details, see :ref:`Description of field resource_tag <sfs_02_0078__table69719318161>`.                                                                                                                                          |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of field **resource_tag**

   .. _sfs_02_0078__table69719318161:

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                             |
   +===========+===========+========+=========================================================================================================================================================================================================================================================================================================================================================================================================+
   | key       | Yes       | String | Specifies the tag key. The value can contain a maximum of 36 characters. This parameter cannot be left empty. It cannot contain the following characters: ASCII (0-31), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (\\), equal signs (=), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | Yes       | String | Specifies the tag value. The value contains a maximum of 43 characters and can be an empty string. It cannot contain ASCII (0-31) or the following characters: ``=*<>\,|/`` It can contain only letters, digits, hyphens (-), and underscores (_).                                                                                                                                                      |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
