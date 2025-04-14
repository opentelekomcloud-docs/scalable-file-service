:original_name: sfs_02_0103.html

.. _sfs_02_0103:

User Signature Authentication
=============================

General Purpose File system signs a request using AK/SK. When a client is sending a request to a general purpose file system, the message header must contain the SK, request time, request type, and other information of the signature.

-  AK: access key ID, which is a unique identifier associated with a secret access key (SK). The AK and SK are used together to obtain an encrypted signature for a request. Format example: **HCY8BGCN1YM5ZWYOK1MH**
-  SK: secret access key, which is used together with the AK to sign requests, identify a request sender, and prevent the request from being modified. Format example: **9zYwf1uabSQY0JTnFqbUqG7vcfqYBaTdXde2GUcq**

General Purpose File System provides the signature calculation method based on the application scenario. For details, see :ref:`Authentication of Signature in a Header <sfs_02_0104>`.

:ref:`Table 1 <sfs_02_0103__en-us_topic_0000001263228774_table1151632183812>` shows the user signature verification process in which a signature is carried in a header. For details about the parameters and code examples of authentication of signature in a header, see :ref:`Authentication of Signature in a Header <sfs_02_0104>`.

.. _sfs_02_0103__en-us_topic_0000001263228774_table1151632183812:

.. table:: **Table 1** Signature calculation and verification procedure of General Purpose File System

   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Procedure                |                                                            | Example                                                                                                                                     |
   +==========================+============================================================+=============================================================================================================================================+
   | Signature calculation    | 1. Construct an HTTP message.                              | PUT /HTTP/1.1                                                                                                                               |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Host: filesystem.sfs3.region.example.com                                                                                                    |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Date: Tue, 04 Jun 2019 06:54:59 GMT                                                                                                         |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Content-Type: text/plain                                                                                                                    |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Content-Length: 5913                                                                                                                        |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 2. Calculate **StringToSign** based on the signature rule. | StringToSign = HTTP-Verb + "\\n" + Content-MD5 + "\\n" + Content-Type + "\\n" + Date + "\\n" + CanonicalizedHeaders + CanonicalizedResource |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 3. Prepare the AK and SK.                                  | AK: \*****\*                                                                                                                                |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | SK: \*****\*                                                                                                                                |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 4. Calculate **Signature**.                                | Signature = Base64( HMAC-SHA1( **SecretAccessKeyID**, UTF-8-Encoding-Of( **StringToSign** ) ) )                                             |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 5. Add a signature header and send the request to SFS.     | PUT /object HTTP/1.1                                                                                                                        |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Host: filesystem.sfs3.region.example.com                                                                                                    |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Date: Tue, 04 Jun 2019 06:54:59 GMT                                                                                                         |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Content-Type: text/plain                                                                                                                    |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Content-Length: 5913                                                                                                                        |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Authorization: OBS **AccessKeyID**:**Signature**                                                                                            |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Signature authentication | 6. Receive the HTTP message.                               | PUT / HTTP/1.1                                                                                                                              |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Host: filesystem.sfs3.region.example.com                                                                                                    |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Date: Tue, 04 Jun 2019 06:54:59 GMT                                                                                                         |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Content-Type: text/plain                                                                                                                    |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Content-Length: 5913                                                                                                                        |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | Authorization: OBS **AccessKeyID**:**Signature**                                                                                            |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 7. Obtain the SK based on the AK in the request.           | Obtain the AK from the authorization header and obtain the SK of the user from IAM.                                                         |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 8. Calculate **StringToSign** based on the signature rule. | StringToSign = HTTP-Verb + "\\n" + Content-MD5 + "\\n" + Content-Type + "\\n" + Date + "\\n" + CanonicalizedHeaders + CanonicalizedResource |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 9. Calculate **Signature**.                                | Signature = Base64( HMAC-SHA1( **SecretAccessKeyID**, UTF-8-Encoding-Of( **StringToSign** ) ) )                                             |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   |                          | 10. Authenticate the signature.                            | Verify that the value of **Signature** in the authorization header is the same as the value of **Signature** calculated by the server.      |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | If the two values are the same, the signature verification is successful.                                                                   |
   |                          |                                                            |                                                                                                                                             |
   |                          |                                                            | If the two values are different, the signature verification fails.                                                                          |
   +--------------------------+------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
