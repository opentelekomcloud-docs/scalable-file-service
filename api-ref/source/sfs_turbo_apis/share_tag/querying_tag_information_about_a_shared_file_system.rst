:original_name: sfs_02_0077.html

.. _sfs_02_0077:

Querying Tag Information About a Shared File System
===================================================

Function
--------

This API is used to query information of all tags about the specified shared file system.

URI
---

-  GET /v1/{project_id}/sfs-turbo/{share_id}/tags
-  Parameter description

   ========== ========= ====== ===========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================================
   project_id Yes       string Specifies the project ID of the operator.
   share_id   Yes       string Specifies the ID of the shared file system.
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

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                          |
   +=======================+=======================+======================================================================================================================+
   | tags                  | List<resource_tag>    | Specifies the tag list. For details, see :ref:`Description of field resource_tag <sfs_02_0077__table7634153341515>`. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
   | sys_tags              | List<resource_tag>    | Only the op_service permission can obtain this field.                                                                |
   |                       |                       |                                                                                                                      |
   |                       |                       | #. Currently, only one resource_tag structure key is used, **\_sys_enterprise_project_id**.                          |
   |                       |                       | #. Currently, **key** contains only one value. **0** indicates the default enterprise project.                       |
   |                       |                       |                                                                                                                      |
   |                       |                       | This field cannot be returned in non-op_service scenarios.                                                           |
   |                       |                       |                                                                                                                      |
   |                       |                       | For details, see :ref:`Description of field resource_tag <sfs_02_0077__table7634153341515>`.                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+

-  Description of field **resource_tag**

   .. _sfs_02_0077__table7634153341515:

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   key       string Specifies the key of the tag.
   value     string Specifies the value of the tag.
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

   +---------------------------+-------------------------------------------------------------+
   | Status Code               | Description                                                 |
   +===========================+=============================================================+
   | 400 Bad Request           | Invalid value.                                              |
   +---------------------------+-------------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                      |
   +---------------------------+-------------------------------------------------------------+
   | 403 Forbidden             | Access to the requested page is forbidden.                  |
   +---------------------------+-------------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                       |
   +---------------------------+-------------------------------------------------------------+
   | 500 Internal Server Error | Failed to complete the request, because of a service error. |
   +---------------------------+-------------------------------------------------------------+
