:original_name: sfs_02_0094.html

.. _sfs_02_0094:

Querying All Tags of a Tenant's Shared File Systems
===================================================

Function
--------

This API is used to query the tag set of a tenant's all shared file systems.

URI
---

-  GET /v1/{project_id}/sfs-turbo/tags
-  Parameter description

   ========== ========= ====== =========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================================
   project_id Yes       String Specifies the project ID of the operator.
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

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                          |
   +=======================+=======================+======================================================================================+
   | tags                  | Array of tags         | Specifies the tag list.                                                              |
   |                       |                       |                                                                                      |
   |                       |                       | For details, see :ref:`Description of field tag <sfs_02_0094__table14385185545214>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

-  Description of the **tag** field

   .. _sfs_02_0094__table14385185545214:

   +-----------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                                                         |
   +===========+==================+=====================================================================================================================================================+
   | key       | String           | Specifies the key of the tag.                                                                                                                       |
   +-----------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | values    | Array of strings | Lists the values of the tag. The value is a list of a tenant's all tag values of shared file systems. Only one of the same tag values is displayed. |
   +-----------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "tags" : [ {
          "key" : "key1",
          "values" : [ "value1", "" ]
        }, {
          "key" : "key2",
          "values" : [ "value1", "value2" ]
        } ]
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
