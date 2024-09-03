:original_name: sfs_02_0011.html

.. _sfs_02_0011:

Authentication
==============

Requests for calling an API can be authenticated using either of the following methods:

-  AK/SK authentication: Requests are encrypted using AK/SK pairs. AK/SK authentication is recommended because it is more secure than token authentication.
-  Token authentication: Requests are authenticated using tokens.

AK/SK Authentication
--------------------

.. note::

   AK/SK authentication supports API requests with a body not larger than 12 MB. For API requests with a larger body, token authentication is recommended.

In AK/SK authentication, AK/SK is used to sign requests and the signature is then added to the requests for authentication.

-  AK: access key ID, which is a unique identifier used in conjunction with a secret access key to sign requests cryptographically.
-  SK: secret access key, which is used in conjunction with an AK to sign requests cryptographically. It identifies a request sender and prevents the request from being modified.

In AK/SK authentication, you can use an AK/SK to sign requests based on the signature algorithm or using the signing SDK.

.. note::

   The signing SDK is only used for signing requests and is different from the SDKs provided by services.

Token Authentication
--------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API. You can obtain a token by calling the `Obtaining User Token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__ API.

IMS is a project-level service. When you call the API, set **auth.scope** in the request body to **project**.

.. code-block::

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",   // IAM user name
                       "password": $ADMIN_PASS,  //IAM user password. You are advised to store it in ciphertext in the configuration file or an environment variable and decrypt it when needed to ensure security.
                       "domain": {
                           "name": "domainname"  // Name of the domain to which the IAM user belongs
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxx"    // Project name
               }
           }
       }
   }

After a token is obtained, the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:

.. code-block:: text

   POST https://{{endpoint}}/v3/auth/projects
   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....
