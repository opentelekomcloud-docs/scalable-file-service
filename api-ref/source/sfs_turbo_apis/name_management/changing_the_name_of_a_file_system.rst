:original_name: ChangeShareName.html

.. _ChangeShareName:

Changing the Name of a File System
==================================

Function
--------

This API is used to change the name of an SFS Turbo file system.

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

   +-------------+-----------+--------------------------------------------------------------+--------------------------------------+
   | Parameter   | Mandatory | Type                                                         | Description                          |
   +=============+===========+==============================================================+======================================+
   | change_name | Yes       | :ref:`ShareName <changesharename__request_sharename>` object | SFS Turbo file system to be modified |
   +-------------+-----------+--------------------------------------------------------------+--------------------------------------+

.. _changesharename__request_sharename:

.. table:: **Table 4** ShareName

   +-----------+-----------+--------+--------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                      |
   +===========+===========+========+==================================================+
   | name      | Yes       | String | Name of the SFS Turbo file system to be modified |
   +-----------+-----------+--------+--------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Changing the name of an SFS Turbo file system to **sfs-turbo-test1**

.. code-block::

   {
     "change_name" : {
       "name" : "sfs-turbo-test1"
     }
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ====================================
Status Code Description
=========== ====================================
204         Request successful
400         Invalid parameter
409         The file system name already exists.
500         Internal error
=========== ====================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
