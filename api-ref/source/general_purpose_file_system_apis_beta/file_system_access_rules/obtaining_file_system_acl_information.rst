:original_name: sfs_02_0117.html

.. _sfs_02_0117:

Obtaining File System ACL Information
=====================================

Function
--------

This API is used to obtain the ACL information of a file system.

URI
---

GET /

.. table:: **Table 1** Query parameter

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   sfsacl    Yes       String /
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============= ========= ====== ==========================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ==========================
   Date          Yes       String The request time.
   Authorization Yes       String The signature information.
   Host          Yes       String The host address.
   ============= ========= ====== ==========================

Response Parameters
-------------------

**Status code: 200**

.. _sfs_02_0117__en-us_topic_0000001263111404_en-us_topic_0000001311159565_response_statement:

.. table:: **Table 3** Response body parameter

   +-----------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                                                                          | Description           |
   +===========+===============================================================================================================================+=======================+
   | Statement | Array of :ref:`Statement <sfs_02_0117__en-us_topic_0000001263111404_en-us_topic_0000001311159565_response_statement>` objects | Unique identification |
   +-----------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. table:: **Table 4** Statement

   +-----------------------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                | Description                                                       |
   +=======================+=====================================================================================================================+===================================================================+
   | Sid                   | String                                                                                                              | The statement ID.                                                 |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Action                | String                                                                                                              | The allowed statement action.                                     |
   |                       |                                                                                                                     |                                                                   |
   |                       |                                                                                                                     | Enumerated values:                                                |
   |                       |                                                                                                                     |                                                                   |
   |                       |                                                                                                                     | -  **FullControl**: read/write                                    |
   |                       |                                                                                                                     | -  **Read**: read-only                                            |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Effect                | String                                                                                                              | The effect specifying that the statement permission is **Allow**. |
   |                       |                                                                                                                     |                                                                   |
   |                       |                                                                                                                     | Enumerated value:                                                 |
   |                       |                                                                                                                     |                                                                   |
   |                       |                                                                                                                     | -  **Allow**                                                      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Condition             | :ref:`Condition <sfs_02_0117__en-us_topic_0000001263111404_en-us_topic_0000001311159565_response_condition>` object | The conditions for a statement to take effect.                    |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+

.. _sfs_02_0117__en-us_topic_0000001263111404_en-us_topic_0000001311159565_response_condition:

.. table:: **Table 5** Condition

   +-------------+------------------+----------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                            |
   +=============+==================+========================================================================================+
   | SourceVpc   | String           | A specified VPC ID.                                                                    |
   +-------------+------------------+----------------------------------------------------------------------------------------+
   | VpcSourceIp | Array of strings | A specified IP address or IP address range. This parameter is currently not supported. |
   +-------------+------------------+----------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET /?sfsacl HTTP/1.1
   Host: example-sfs-01.sfs3.example.region.com:443
   Date: Wed, 07 Jun 2023 03:31:46 GMT
   Authorization: OBS FNEX1B77SXDIB3TFMSZZ:eUqPlHnPDWGDTlgyLmsALA86wys=

Example Response
----------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   Content-Type: application/json
   Content-Length: 131
   Date: Wed, 07 Jun 2023 03:31:59 GMT
   X-Obs-Request-Id: 0000018893E94B65C046B527778F8F14
   X-Obs-Id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSc2lEdSHcA04319WknB1DD5BdBKuGr1
   {
       "Statement": [
           {
               "Condition": {
                   "SourceVpc": "f85adabc-a387-4d1d-94cf-65ef9034f752"
               },
               "Action": "FullControl",
               "Effect": "Allow",
               "Sid": ""
           }
       ]
   }

Status Codes
------------

=========== ================================
Status Code Description
=========== ================================
200         The file system ACL is obtained.
=========== ================================

Error Codes
-----------

See :ref:`General Purpose File System Error Codes <sfs_02_0119>`.
