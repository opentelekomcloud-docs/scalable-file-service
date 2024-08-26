:original_name: ChangeSecurityGroup.html

.. _ChangeSecurityGroup:

Changing the Security Group Associated with a File System
=========================================================

Function
--------

This API is used to change the security group associated with an SFS Turbo file system. Security group change is an asynchronous task. You can check whether the security group is changed based on the value of **sub_status** returned after calling the API to query details of a file system. If value **232** is returned, the security group has been changed.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/action

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ==============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==============
   project_id Yes       String Project ID
   share_id   Yes       String File system ID
   ========== ========= ====== ==============

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   X-Auth-Token Yes       String Account token
   Content-Type Yes       String MIME type
   ============ ========= ====== =============

.. table:: **Table 3** Request body parameters

   +-----------------------+-----------+--------------------------------------------------------------------------------------+-------------------------------------+
   | Parameter             | Mandatory | Type                                                                                 | Description                         |
   +=======================+===========+======================================================================================+=====================================+
   | change_security_group | Yes       | :ref:`ChangeSecurityGroup <changesecuritygroup__request_changesecuritygroup>` object | Object of **change_security_group** |
   +-----------------------+-----------+--------------------------------------------------------------------------------------+-------------------------------------+

.. _changesecuritygroup__request_changesecuritygroup:

.. table:: **Table 4** ChangeSecurityGroup

   +-------------------+-----------+--------+----------------------------------------+
   | Parameter         | Mandatory | Type   | Description                            |
   +===================+===========+========+========================================+
   | security_group_id | Yes       | String | ID of the security group to be changed |
   +-------------------+-----------+--------+----------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameters

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   id        String ID of the SFS Turbo file system
   ========= ====== ===============================

Example Requests
----------------

Changing the security group of a file system (target security group ID **26f6b565-240e-43c3-8867-03f0bd975433**)

.. code-block::

   {
     "change_security_group" : {
       "security_group_id" : "26f6b565-240e-43c3-8867-03f0bd975433"
     }
   }

Example Responses
-----------------

**Status code: 202**

ID of the SFS Turbo file system

.. code-block::

   {
     "id" : "67d4bd5e-7b2f-4c24-9a0b-c0038940c6f8"
   }

Status Codes
------------

=========== ===============================
Status Code Description
=========== ===============================
202         ID of the SFS Turbo file system
=========== ===============================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
