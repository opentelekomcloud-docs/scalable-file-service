:original_name: ChangeSecurityGroup.html

.. _ChangeSecurityGroup:

Changing the Security Group Associated with a File System
=========================================================

Function
--------

This API is used to change the security group associated with an SFS Turbo file system. Changing the security group is an asynchronous task. You can call the API for querying details of a file system and view the value of **sub_status** returned to check whether the security group change is successful. If value **232** is returned, the security group has been changed.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/action

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================
   project_id Yes       String The project ID.
   share_id   Yes       String The file system ID.
   ========== ========= ====== ===================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ==================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ==================
   X-Auth-Token Yes       String The account token.
   Content-Type Yes       String The MIME type.
   ============ ========= ====== ==================

.. table:: **Table 3** Request body parameters

   +-----------------------+-----------+--------------------------------------------------------------------------------------+---------------------------------------+
   | Parameter             | Mandatory | Type                                                                                 | Description                           |
   +=======================+===========+======================================================================================+=======================================+
   | change_security_group | Yes       | :ref:`ChangeSecurityGroup <changesecuritygroup__request_changesecuritygroup>` object | The **change_security_group** object. |
   +-----------------------+-----------+--------------------------------------------------------------------------------------+---------------------------------------+

.. _changesecuritygroup__request_changesecuritygroup:

.. table:: **Table 4** ChangeSecurityGroup

   ================= ========= ====== =================================
   Parameter         Mandatory Type   Description
   ================= ========= ====== =================================
   security_group_id Yes       String The ID of the new security group.
   ================= ========= ====== =================================

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameters

   ========= ====== =============================
   Parameter Type   Description
   ========= ====== =============================
   id        String The SFS Turbo file system ID.
   ========= ====== =============================

Example Requests
----------------

Changing the security group of a file system (new security group ID **26f6b565-240e-43c3-8867-03f0bd975433**)

.. code-block::

   {
     "change_security_group" : {
       "security_group_id" : "26f6b565-240e-43c3-8867-03f0bd975433"
     }
   }

Example Responses
-----------------

**Status code: 202**

The SFS Turbo file system ID.

.. code-block::

   {
     "id" : "67d4bd5e-7b2f-4c24-9a0b-c0038940c6f8"
   }

Status Codes
------------

=========== =============================
Status Code Description
=========== =============================
202         The SFS Turbo file system ID.
=========== =============================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
