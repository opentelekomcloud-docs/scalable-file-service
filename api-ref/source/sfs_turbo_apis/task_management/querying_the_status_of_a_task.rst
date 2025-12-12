:original_name: ShowJobDetail.html

.. _ShowJobDetail:

Querying the Status of a Task
=============================

Function
--------

This API is used to query the execution status of the SFS Turbo asynchronous API.

URI
---

GET /v1/{project_id}/sfs-turbo/jobs/{job_id}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===============
   project_id Yes       String The project ID.
   job_id     Yes       String job ID
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

   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                              | Description                                                                             |
   +=======================+===================================================================================+=========================================================================================+
   | status                | String                                                                            | The task status.                                                                        |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | Enumerated values:                                                                      |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **success**: successful                                                              |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **failed**: failed                                                                   |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **waiting**: waiting for execution                                                   |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **running**: running                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | job_id                | String                                                                            | The task ID.                                                                            |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | job_type              | String                                                                            | The task type.                                                                          |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | Enumerated values:                                                                      |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **create_share**: creating a file system                                             |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **hpc_create_share**: creating a file system                                         |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **delete_share**: deleting a file system                                             |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **extend_share**: expanding the capacity of a file system                            |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **change_security_group**: changing the security group associated with a file system |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **create_obs_target**: adding a storage backend                                      |
   |                       |                                                                                   |                                                                                         |
   |                       |                                                                                   | -  **delete_obs_target**: removing a storage backend                                    |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | begin_time            | String                                                                            | The task start time in UTC format, for example, **2016-01-02 15:04:05**.                |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | end_time              | String                                                                            | The task end time in UTC format, for example, **2016-01-02 15:04:05**.                  |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | error_code            | String                                                                            | The error code returned if the task execution fails.                                    |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | fail_reason           | String                                                                            | The cause of the task execution failure.                                                |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | sub_jobs              | Array of :ref:`GetSubJobDetail <showjobdetail__response_getsubjobdetail>` objects | The subtask list.                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+

.. _showjobdetail__response_getsubjobdetail:

.. table:: **Table 5** GetSubJobDetail

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                             |
   +=======================+=======================+=========================================================================================+
   | status                | String                | The task status.                                                                        |
   |                       |                       |                                                                                         |
   |                       |                       | Enumerated values:                                                                      |
   |                       |                       |                                                                                         |
   |                       |                       | -  **success**: successful                                                              |
   |                       |                       |                                                                                         |
   |                       |                       | -  **failed**: failed                                                                   |
   |                       |                       |                                                                                         |
   |                       |                       | -  **waiting**: waiting for execution                                                   |
   |                       |                       |                                                                                         |
   |                       |                       | -  **running**: running                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | job_id                | String                | The subtask ID.                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | job_type              | String                | The subtask type.                                                                       |
   |                       |                       |                                                                                         |
   |                       |                       | Enumerated values:                                                                      |
   |                       |                       |                                                                                         |
   |                       |                       | -  **create_share**: creating a file system                                             |
   |                       |                       |                                                                                         |
   |                       |                       | -  **hpc_create_share**: creating a file system                                         |
   |                       |                       |                                                                                         |
   |                       |                       | -  **delete_share**: deleting a file system                                             |
   |                       |                       |                                                                                         |
   |                       |                       | -  **extend_share**: expanding the capacity of a file system                            |
   |                       |                       |                                                                                         |
   |                       |                       | -  **change_security_group**: changing the security group associated with a file system |
   |                       |                       |                                                                                         |
   |                       |                       | -  **create_obs_target**: adding a storage backend                                      |
   |                       |                       |                                                                                         |
   |                       |                       | -  **delete_obs_target**: removing a storage backend                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | begin_time            | String                | The subtask start time in UTC format, for example, **2016-01-02 15:04:05**.             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | end_time              | String                | The subtask end time in UTC format, for example, **2016-01-02 15:04:05**.               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | error_code            | String                | The error code returned if the subtask execution fails.                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
   | fail_reason           | String                | The cause of the subtask execution failure.                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 7** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 404**

.. table:: **Table 8** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 9** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 500**

.. table:: **Table 10** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 11** Response body parameters

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

Response body parameter

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

=========== =======================
Status Code Description
=========== =======================
200         Response body parameter
400         Client error
404         Resource not found
500         Internal error
=========== =======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
