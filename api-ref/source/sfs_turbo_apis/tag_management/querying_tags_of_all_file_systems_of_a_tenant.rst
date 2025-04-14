:original_name: ListSharedTags.html

.. _ListSharedTags:

Querying Tags of All File Systems of a Tenant
=============================================

Function
--------

This API is used to query the tags of all file systems of a tenant.

URI
---

GET /v1/{project_id}/sfs-turbo/tags

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   ========= ========= ======= =======================
   Parameter Mandatory Type    Description
   ========= ========= ======= =======================
   limit     No        Integer Number of returned tags
   offset    No        Integer Tag query offset
   ========= ========= ======= =======================

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   X-Auth-Token Yes       String Account token
   Content-Type Yes       String MIME type
   ============ ========= ====== =============

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------------------------------------------------------------+-------------+
   | Parameter | Type                                                       | Description |
   +===========+============================================================+=============+
   | tags      | Array of :ref:`Tag <listsharedtags__response_tag>` objects | Tag list    |
   +-----------+------------------------------------------------------------+-------------+

.. _listsharedtags__response_tag:

.. table:: **Table 5** Tag

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================================================+
   | key                   | String                | Tag key.                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                       |
   |                       |                       | A key can contain a maximum of 128 characters and cannot be left blank.                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values                | Array of strings      | Tag values. Each value can contain a maximum of 255 characters. An empty list of values can match with any value. All values of a tag key are in the OR relationship. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Query tags of all file systems in the project whose ID is **e1e45b08f3ea4480ab4655ef9c7160ba**

.. code-block:: text

   GET HTTPS://{endpoint}/v1/e1e45b08f3ea4480ab4655ef9c7160ba/sfs-turbo/tags

Example Responses
-----------------

**Status code: 200**

Response body for querying a file system

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

=========== ========================================
Status Code Description
=========== ========================================
200         Response body for querying a file system
=========== ========================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
