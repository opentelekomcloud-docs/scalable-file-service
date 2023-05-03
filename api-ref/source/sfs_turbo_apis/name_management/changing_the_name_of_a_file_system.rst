:original_name: en-us_topic_0000001537629949.html

.. _en-us_topic_0000001537629949:

Changing the Name of a File System
==================================

Function
--------

This API is used to change the name of a file system.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/action

.. table:: **Table 1** Path parameters

   ========== ========= ====== =============================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =============================
   project_id Yes       String Specifies the project ID.
   share_id   Yes       String Specifies the file system ID.
   ========== ========= ====== =============================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ============================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ============================
   X-Auth-Token Yes       String Specifies the account token.
   Content-Type Yes       String Specifies the MIME type.
   ============ ========= ====== ============================

.. table:: **Table 3** Request body parameter

   +-------------+-----------+---------------------------------------------------------------------------+------------------------------------------------------------------+
   | Parameter   | Mandatory | Type                                                                      | Description                                                      |
   +=============+===========+===========================================================================+==================================================================+
   | change_name | Yes       | :ref:`ShareName <en-us_topic_0000001537629949__request_sharename>` object | Specifies the SFS Turbo file system you want to change the name. |
   +-------------+-----------+---------------------------------------------------------------------------+------------------------------------------------------------------+

.. _en-us_topic_0000001537629949__request_sharename:

.. table:: **Table 4** ShareName

   +-----------+-----------+--------+------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                  |
   +===========+===========+========+==============================================================================+
   | name      | Yes       | String | Specifies the name of the SFS Turbo file system you want to change the name. |
   +-----------+-----------+--------+------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block::

   {
     "change_name" : {
       "name" : "sfs-turbo-test1"
     }
   }

Example Response
----------------

None

Status Codes
------------

=========== ================================
Status Code Description
=========== ================================
204         Request successful.
400         Invalid parameters.
500         Internal error.
409         File system name already exists.
=========== ================================
