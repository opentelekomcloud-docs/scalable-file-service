:original_name: sfs_02_0077.html

.. _sfs_02_0077:

Querying Tags of a File System
==============================

Function
--------

This API is used to query all tags of an SFS Turbo file system.

URI
---

-  GET /v1/{project_id}/sfs-turbo/{share_id}/tags
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

   ========= ====== ========================
   Parameter Type   Description
   ========= ====== ========================
   key       String Specifies the tag key.
   value     String Specifies the tag value.
   ========= ====== ========================

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
