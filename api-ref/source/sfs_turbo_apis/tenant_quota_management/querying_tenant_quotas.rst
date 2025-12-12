:original_name: ShowQuota.html

.. _ShowQuota:

Querying Tenant Quotas
======================

Function
--------

Querying tenant quotas

URI
---

GET /v1/{project_id}/sfs-turbo/quotas

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===============
   project_id Yes       String The project ID.
   ========== ========= ====== ===============

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ==================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ==================
   X-Auth-Token Yes       String The account token.
   Content-Type Yes       String The MIME type.
   ============ ========= ====== ==================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------------+------------------------+
   | Parameter | Type                                                                    | Description            |
   +===========+=========================================================================+========================+
   | quotas    | :ref:`ShowQuotaResource <showquota__response_showquotaresource>` object | Querying tenant quotas |
   +-----------+-------------------------------------------------------------------------+------------------------+

.. _showquota__response_showquotaresource:

.. table:: **Table 5** ShowQuotaResource

   +-----------+---------------------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                                      | Description                |
   +===========+===========================================================================+============================+
   | resources | Array of :ref:`QuotaResource <showquota__response_quotaresource>` objects | The tenant resource quota. |
   +-----------+---------------------------------------------------------------------------+----------------------------+

.. _showquota__response_quotaresource:

.. table:: **Table 6** QuotaResource

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                     |
   +=======================+=======================+=================================================================================================================================+
   | type                  | String                | The tenant's resource type. **shares** indicates the file system quantity, and **capacity** indicates the file system capacity. |
   |                       |                       |                                                                                                                                 |
   |                       |                       | Enumeration values:                                                                                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **shares**                                                                                                                   |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **capacity**                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | used                  | Integer               | The used quota.                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | quota                 | Integer               | The total quota.                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | unit                  | String                | The quota unit.                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 8** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 500**

.. table:: **Table 9** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 10** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "quotas" : {
       "resources" : [ {
         "type" : "shares",
         "used" : 5,
         "quota" : 400
       }, {
         "type" : "capacity",
         "used" : 0,
         "quota" : 20,
         "unit" : "GB"
       } ]
     }
   }

**Status code: 400**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0001",
     "errMsg" : "parameter error"
   }

**Status code: 500**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0005",
     "errMsg" : "Internal server error"
   }

Status Codes
------------

=========== ==============
Status Code Description
=========== ==============
200         Success
400         Error response
500         Error response
=========== ==============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
