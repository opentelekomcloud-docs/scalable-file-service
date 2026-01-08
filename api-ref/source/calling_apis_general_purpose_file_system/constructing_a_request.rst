:original_name: sfs_02_0101.html

.. _sfs_02_0101:

Constructing a Request
======================

This section describes the structure of a REST API request.

Request URI
-----------

SFS uses URI to locate specific file systems and their parameters. Use URIs when you want to operate resources.

The following provides a common URI format. The parameters in square brackets [ ] are optional.

**protocol://[filesystem.\ ]\ domain[:port]/[?param]**

.. table:: **Table 1** URI parameters

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                                                                                                                                                   | Mandatory             |
   +=======================+===============================================================================================================================================================================================================================================================================================================================+=======================+
   | protocol              | Protocol used for sending requests, which can be either HTTP or HTTPS. HTTPS is a protocol that ensures secure access to resources. SFS supports both HTTP and HTTPS.                                                                                                                                                         | Yes                   |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | filesystem            | Resource path of a file system, identifying only one file system in SFS                                                                                                                                                                                                                                                       | No                    |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | domain                | Domain name or IP address of the server for saving resources                                                                                                                                                                                                                                                                  | Yes                   |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | port                  | Port enabled for protocols used for sending requests. The value varies with software server deployment. If no port number is specified, the protocol uses the default value. Each transmission protocol has its default port number. For example, HTTP uses port number **80** and HTTPS uses port number **443** by default. | No                    |
   |                       |                                                                                                                                                                                                                                                                                                                               |                       |
   |                       | In SFS, HTTP port number is **80** and that of HTTPS is **443**.                                                                                                                                                                                                                                                              |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | param                 | A specific resource contained by a file system. Default value of this parameter indicates that the file system itself is obtained.                                                                                                                                                                                            | No                    |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. important::

   All API requests except those for the file system list must contain the file system name. Based on the DNS resolution performance and reliability, SFS requires that the file system name must be placed in front of the **domain** when a request carrying a file system name is constructed to form a third-level domain name, also mentioned as virtual hosting access domain name.

Request Method
--------------

HTTP methods, which are also called operations or actions, specify the type of operations that you are requesting.

.. table:: **Table 2** REST request methods supported by General Purpose File System

   +---------+------------------------------------------------------------------------------------------+
   | Method  | Description                                                                              |
   +=========+==========================================================================================+
   | GET     | Requests the server to return specific resources, for example, to list file systems.     |
   +---------+------------------------------------------------------------------------------------------+
   | PUT     | Requests the server to update specific resources, for example, creating file systems.    |
   +---------+------------------------------------------------------------------------------------------+
   | POST    | Requests a server to add resources or perform special operations.                        |
   +---------+------------------------------------------------------------------------------------------+
   | DELETE  | Requests the server to delete specified resources, for example, file systems.            |
   +---------+------------------------------------------------------------------------------------------+
   | HEAD    | Same as GET except that the server must return only the response header.                 |
   +---------+------------------------------------------------------------------------------------------+
   | OPTIONS | Requests the server to check whether the user has the permissions to operate a resource. |
   +---------+------------------------------------------------------------------------------------------+

Request Headers
---------------

Refers to optional and additional request fields, for example a field required by a specific URI or HTTP method. :ref:`Table 3 <sfs_02_0101__en-us_topic_0000001263228726_table25197309>` describes some common request header fields.

.. _sfs_02_0101__en-us_topic_0000001263228726_table25197309:

.. table:: **Table 3** Common request headers

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Header                | Description                                                                                                                   | Mandatory              |
   +=======================+===============================================================================================================================+========================+
   | Authorization         | Signature information contained in a request message                                                                          | Conditionally required |
   |                       |                                                                                                                               |                        |
   |                       | Type: string                                                                                                                  |                        |
   |                       |                                                                                                                               |                        |
   |                       | No default value.                                                                                                             |                        |
   |                       |                                                                                                                               |                        |
   |                       | Conditional: optional for anonymous requests and required for other requests.                                                 |                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Content-Length        | The message length (excluding headers) defined in RFC 2616                                                                    | Conditionally required |
   |                       |                                                                                                                               |                        |
   |                       | Type: string                                                                                                                  |                        |
   |                       |                                                                                                                               |                        |
   |                       | No default value.                                                                                                             |                        |
   |                       |                                                                                                                               |                        |
   |                       | Conditional: required for PUT requests and those requests that load XML content.                                              |                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Content-Type          | The content type of the requested resource, for example, **text**/**plain**                                                   | No                     |
   |                       |                                                                                                                               |                        |
   |                       | Type: string                                                                                                                  |                        |
   |                       |                                                                                                                               |                        |
   |                       | No default value.                                                                                                             |                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Date                  | The time when a request is initiated, for example, **Wed, 27 Jun 2018 13:39:15 +0000**.                                       | Conditionally required |
   |                       |                                                                                                                               |                        |
   |                       | Type: string                                                                                                                  |                        |
   |                       |                                                                                                                               |                        |
   |                       | No default value.                                                                                                             |                        |
   |                       |                                                                                                                               |                        |
   |                       | Conditional: optional for anonymous requests or those requests containing header **x-obs-date**, required for other requests. |                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Host                  | The host address, for example, **filesystem.sfs3.region.example.com**.                                                        | Yes                    |
   |                       |                                                                                                                               |                        |
   |                       | Type: string                                                                                                                  |                        |
   |                       |                                                                                                                               |                        |
   |                       | No default value.                                                                                                             |                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------+

(Optional) Request Body
-----------------------

A request body is generally sent in a structured format (for example, JSON or XML). It corresponds to **Content-Type** in the request header and is used to transfer content other than the request header.

The request body varies according to the APIs. Certain APIs do not require the request body, such as the GET and DELETE APIs.

Sending a Request
-----------------

There are two methods to initiate requests based on the constructed request messages:

-  cURL

   cURL is a command-line tool used to perform URL operations and transmit information. cURL acts as an HTTP client that can send HTTP requests to the server and receive response messages. cURL is applicable to API debugging. For more information about cURL, visit https://curl.haxx.se/. cURL cannot calculate signatures. When cURL is used, only anonymous public SFS resources can be accessed.

-  Coding

   You can use code to make API calls, and to assemble, send, and process request messages. It can be implemented by coding.
