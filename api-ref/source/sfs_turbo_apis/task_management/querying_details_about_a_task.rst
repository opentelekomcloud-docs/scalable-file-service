:original_name: ShowJobDetail.html

.. _ShowJobDetail:

Querying Details About a Task
=============================

Function
--------

This API is used to query the execution status of an SFS Turbo asynchronous task.

URI
---

GET /v1/{project_id}/sfs-turbo/jobs/{job_id}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   job_id     Yes       String job ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   X-Auth-Token Yes       String Account token
   Content-Type Yes       String MIME type
   ============ ========= ====== =============

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   X-request-id String Request ID
   ============ ====== ===========

.. table:: **Table 4** Response body parameters

   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | Parameter   | Type                                                                              | Description                                                                    |
   +=============+===================================================================================+================================================================================+
   | status      | String                                                                            | Task status, which can be **success**, **running**, **failed**, or **waiting** |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | job_id      | String                                                                            | Task ID                                                                        |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | job_type    | String                                                                            | Task type                                                                      |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | begin_time  | String                                                                            | Task start time in UTC format, for example, **'2016-01-02 15:04:05**           |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | end_time    | String                                                                            | Task end time in UTC format, for example, **'2016-01-02 15:04:05**             |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | error_code  | String                                                                            | Error code returned if the task execution fails                                |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | fail_reason | String                                                                            | Cause of the task execution failure                                            |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | sub_jobs    | Array of :ref:`GetSubJobDetail <showjobdetail__response_getsubjobdetail>` objects | List of subtasks                                                               |
   +-------------+-----------------------------------------------------------------------------------+--------------------------------------------------------------------------------+

.. _showjobdetail__response_getsubjobdetail:

.. table:: **Table 5** GetSubJobDetail

   +-------------+--------+-----------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                       |
   +=============+========+===================================================================================+
   | status      | String | Subtask status, which can be **success**, **running**, **failed**, or **waiting** |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | job_id      | String | Task ID                                                                           |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | job_type    | String | Subtask type                                                                      |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | begin_time  | String | Task start time in UTC format, for example, **'2016-01-02 15:04:05**              |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | end_time    | String | Task end time in UTC format, for example, **'2016-01-02 15:04:05**                |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | error_code  | String | Error code returned if the task execution fails                                   |
   +-------------+--------+-----------------------------------------------------------------------------------+
   | fail_reason | String | Cause of the task execution failure                                               |
   +-------------+--------+-----------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   errCode   String Error code
   errMsg    String Error description
   ========= ====== =================

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   errCode   String Error code
   errMsg    String Error description
   ========= ====== =================

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   errCode   String Error code
   errMsg    String Error description
   ========= ====== =================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Response body parameters

.. code-block::

   {
     "job_id" : "26f6b565-xxxx-XXXX-xxxx-03f0bd975433",
     "status" : "success",
     "job_type" : "bind_ldap",
     "begin_time" : "2023-07-26 09:33:58",
     "end_time" : "2023-07-26 09:33:58"
   }

**Status code: 400**

Client error

.. code-block::

   {
     "errCode" : "SFS.TURBO.0001",
     "errMsg" : "parameter error"
   }

**Status code: 404**

Resource not found

.. code-block::

   {
     "errCode" : "SFS.TURBO.0001",
     "errMsg" : "parameter error"
   }

**Status code: 500**

Internal error

.. code-block::

   {
     "errCode" : "SFS.TURBO.0005",
     "errMsg" : "Internal server error"
   }

Status Codes
------------

=========== ========================
Status Code Description
=========== ========================
200         Response body parameters
400         Client error
404         Resource not found
500         Internal error
=========== ========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
