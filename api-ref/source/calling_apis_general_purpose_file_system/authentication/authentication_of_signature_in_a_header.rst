:original_name: sfs_02_0104.html

.. _sfs_02_0104:

Authentication of Signature in a Header
=======================================

For all General Purpose File System API operations, the identity authentication can be done by carrying signatures in headers.

In the header, the signature is carried in the authorization header field of the HTTP message. The format of the message header is as follows:

.. code-block::

   Authorization: OBS AccessKeyID:signature

The signature algorithm process is as follows:

1. Construct the request character string (StringToSign).

2. Perform UTF-8 encoding on the result obtained from the preceding step.

3. Use the SK to perform the HMAC-SHA1 signature calculation on the result obtained from step 2.

4. Perform Base64 encoding on the result of step 3 to obtain the signature.

The StringToSign is constructed according to the following rules. :ref:`Table 1 <sfs_02_0104__en-us_topic_0000001311148725_table34479832212511>` describes the parameters.

.. code-block::

   StringToSign =
       HTTP-Verb + "\n" +
       Content-MD5 + "\n" +
       Content-Type + "\n" +
       Date + "\n" +
       CanonicalizedHeaders + CanonicalizedResource

.. _sfs_02_0104__en-us_topic_0000001311148725_table34479832212511:

.. table:: **Table 1** Parameters required for constructing a StringToSign

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                              |
   +===================================+==========================================================================================================================================================================================================================================================================================================================================================================+
   | HTTP-Verb                         | An HTTP request method supported by the REST API. The value can be an HTTP verb such as **PUT**, **GET**, or **DELETE**.                                                                                                                                                                                                                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-MD5                       | The base64-encoded 128-bit MD5 digest of the message according to RFC 1864. This parameter can be empty.                                                                                                                                                                                                                                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type                      | The message type, for example, **text/plain**.                                                                                                                                                                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   | If a request does not contain this header field, this parameter will be processed as an empty string.                                                                                                                                                                                                                                                                    |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date                              | The time when a request is initiated. This parameter uses the RFC 1123 time format. If the deviation between the time specified by this parameter and the server time is over 15 minutes, the server returns error 403.                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   | This parameter is an empty string when the **x-obs-date** is specified.                                                                                                                                                                                                                                                                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CanonicalizedHeaders              | The general purpose file system request header field in an HTTP request header, referring to header fields started with **x-obs-**, for example, **x-obs-date**, **x-obs-acl**, and **x-obs-meta-\***.                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   | #. All characters of keywords in a request header field must be converted to lowercase letters (content values must be case sensitive, for example, **x-obs-storage-class:STANDARD**). If a request contains multiple header fields, these fields should be organized by keyword in the alphabetical order from a to z.                                                  |
   |                                   | #. If multiple header fields in a request have the same prefix, combine the header fields into one. For example, **x-obs-meta-name:name1** and **x-obs-meta-name:name2** should be reorganized into **x-obs-meta-name:name1,name2**. Use comma to separate the values.                                                                                                   |
   |                                   | #. Keywords in the request header field cannot contain non-ASCII or unrecognizable characters, which are also not advisable for values in the request header field. If the two types of characters are necessary, they should be encoded and decoded on the client side. Either URL encoding or Base64 encoding is acceptable, but the server does not perform decoding. |
   |                                   | #. Delete meaningless spaces and tabs in a header field. For example, **x-obs-meta-name: name** (with a meaningless space in the front of **name**) must be changed to **x-obs-meta-name:name**.                                                                                                                                                                         |
   |                                   | #. Each header field occupies a separate line.                                                                                                                                                                                                                                                                                                                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CanonicalizedResource             | The general purpose file system specified by an HTTP request. This parameter is constructed as follows:                                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   | <File system name + Object name> + [Subresource 1] + [Subresource 2] + ...                                                                                                                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   | #. File system name and object name, for example, /filesystem/object. If no object name is specified, the entire file system is listed, for example, **/filesystem/**. If file system name is not specified either, the value of this field is **/**.                                                                                                                    |
   |                                   | #. If a subresource (such as **?sfsacl**) exists, the subresource must be added.                                                                                                                                                                                                                                                                                         |
   |                                   | #. If there are multiple subresources, sort them in the alphabetical order from a to z, and use **&** to combine the subresources.                                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
   |                                   |    -  A subresource is unique. Do not add subresources with the same keyword (for example, **key=value1&key=value2**) in the same request URL. In this case, signature is computed only based on the first subresource, and only the value of the first subresource takes effect on the actual service.                                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following table provides some examples of generating StringToSign.

.. table:: **Table 2** Obtaining the ACL of a file system

   +------------------------------------------+-----------------------------------+
   | Request Header                           | StringToSign                      |
   +==========================================+===================================+
   | GET /?sfsacl HTTP/1.1                    | GET \\n                           |
   |                                          |                                   |
   | Host: filesystem.sfs3.region.example.com | ``\n``                            |
   |                                          |                                   |
   | Date: Sat, 12 Oct 2015 08:12:38 GMT      | ``\n``                            |
   |                                          |                                   |
   |                                          | Sat, 12 Oct 2015 08:12:38 GMT\\n  |
   |                                          |                                   |
   |                                          | /filesystem/?sfsacl               |
   +------------------------------------------+-----------------------------------+

Content-MD5 Algorithm in Java
-----------------------------

::

   import java.security.MessageDigest;
   import sun.misc.BASE64Encoder;
   import java.io.UnsupportedEncodingException;
   import java.security.NoSuchAlgorithmException;

   public class Md5{
        public static void main(String[] args) {
             try {
                    String exampleString = "blog";
                    MessageDigest messageDigest = MessageDigest.getInstance("MD5");
                    BASE64Encoder encoder = new BASE64Encoder();
                    String contentMd5 = encoder.encode(messageDigest.digest(exampleString.getBytes("utf-8")));
                    System.out.println("Content-MD5:" + contentMd5);
             } catch (NoSuchAlgorithmException | UnsupportedEncodingException e)
             {
                    e.printStackTrace();
             }
        }
   }

The signature is generated as follows based on the StringToSign and SK. The hash-based message authentication code algorithm (HMAC algorithm) is used to generate the signature.

.. code-block::

   Signature = Base64( HMAC-SHA1( YourSecretAccessKeyID, UTF-8-Encoding-Of( StringToSign ) ) )

For example, to create a file system named **newfilesystem2** in a region, the client request format is as follows:

.. code-block:: text

   PUT / HTTP/1.1
   Host: newfilesystem2.sfs3.region.example.com
   Content-Length: length
   Date: Fri, 06 Jul 2018 03:45:51 GMT
   x-obs-acl:private
   x-obs-storage-class:STANDARD
   Authorization: OBS UDSIAMSTUBTEST000254:ydH8ffpcbS6YpeOMcEZfn0wE90c=

   <CreateBucketConfiguration xmlns="http://obs.otc.t-systems.com/doc/2016-01-01/">
       <Location>region</Location>
   </CreateBucketConfiguration>

Signature Algorithm in Java
---------------------------

::

   import java.io.UnsupportedEncodingException;
   import java.net.URLEncoder;
   import java.security.InvalidKeyException;
   import java.security.NoSuchAlgorithmException;
   import java.util.ArrayList;
   import java.util.Arrays;
   import java.util.Base64;
   import java.util.Collections;
   import java.util.HashMap;
   import java.util.List;
   import java.util.Locale;
   import java.util.Map;
   import java.util.TreeMap;

   import javax.crypto.Mac;
   import javax.crypto.spec.SecretKeySpec;

   import org.omg.CosNaming.IstringHelper;


   public class SignDemo {

       private static final String SIGN_SEP = "\n";

       private static final String SFS_PREFIX = "x-obs-";

       private static final String DEFAULT_ENCODING = "UTF-8";

       private static final List<String> SUB_RESOURCES = Collections.unmodifiableList(Arrays.asList(
               "CDNNotifyConfiguration", "acl", "append", "attname", "backtosource", "cors", "customdomain", "delete",
               "deletebucket", "directcoldaccess", "encryption", "inventory", "length", "lifecycle", "location", "logging",
               "metadata", "modify", "name", "notification", "orchestration", "partNumber", "policy", "position", "quota",
               "rename", "replication", "requestPayment", "response-cache-control", "response-content-disposition",
               "response-content-encoding", "response-content-language", "response-content-type", "response-expires",
               "restore", "select", " storageClass", "storagePolicy", "storageinfo", "tagging", "torrent", "truncate",
               "uploadId", "uploads", "versionId", "versioning", "versions", "website", "x-image-process",
               "x-image-save-bucket", "x-image-save-object", "x-obs-security-token"));

       private String ak;

       private String sk;

        public String urlEncode(String input) throws UnsupportedEncodingException
       {
           return URLEncoder.encode(input, DEFAULT_ENCODING)
           .replaceAll("%7E", "~") //for browser
           .replaceAll("%2F", "/")
           .replaceAll("%20", "+");
       }

       private String join(List<?> items, String delimiter)
       {
           StringBuilder sb = new StringBuilder();
           for (int i = 0; i < items.size(); i++)
           {
       String item = items.get(i).toString();
               sb.append(item);
               if (i < items.size() - 1)
               {
                   sb.append(delimiter);
               }
           }
           return sb.toString();
       }

       private boolean isValid(String input) {
           return input != null && !input.equals("");
       }

       public String hamcSha1(String input) throws NoSuchAlgorithmException, InvalidKeyException, UnsupportedEncodingException {
           SecretKeySpec signingKey = new SecretKeySpec(this.sk.getBytes(DEFAULT_ENCODING), "HmacSHA1");
           Mac mac = Mac.getInstance("HmacSHA1");
           mac.init(signingKey);
           return Base64.getEncoder().encodeToString(mac.doFinal(input.getBytes(DEFAULT_ENCODING)));
       }

       private String stringToSign(String httpMethod, Map<String, String[]> headers, Map<String, String> queries,
               String bucketName, String objectName) throws Exception{
           String contentMd5 = "";
           String contentType = "";
           String date = "";

           TreeMap<String, String> canonicalizedHeaders = new TreeMap<String, String>();

           String key;
           List<String> temp = new ArrayList<String>();
           for(Map.Entry<String, String[]> entry : headers.entrySet()) {
               key = entry.getKey();
               if(key == null || entry.getValue() == null || entry.getValue().length == 0) {
                   continue;
               }

               key = key.trim().toLowerCase(Locale.ENGLISH);
               if(key.equals("content-md5")) {
                   contentMd5 = entry.getValue()[0];
                   continue;
               }

               if(key.equals("content-type")) {
                   contentType = entry.getValue()[0];
                   continue;
               }

               if(key.equals("date")) {
                   date = entry.getValue()[0];
                   continue;
               }

               if(key.startsWith(OBS_PREFIX)) {

                   for(String value : entry.getValue()) {
                       if(value != null) {
                           temp.add(value.trim());
                       }
                   }
                   canonicalizedHeaders.put(key, this.join(temp, ","));
                   temp.clear();
               }
           }

           if(canonicalizedHeaders.containsKey("x-obs-date")) {
               date = "";
           }


           // handle method/content-md5/content-type/date
           StringBuilder stringToSign = new StringBuilder();
           stringToSign.append(httpMethod).append(SIGN_SEP)
               .append(contentMd5).append(SIGN_SEP)
               .append(contentType).append(SIGN_SEP)
               .append(date).append(SIGN_SEP);

           // handle canonicalizedHeaders
           for(Map.Entry<String, String> entry : canonicalizedHeaders.entrySet()) {
               stringToSign.append(entry.getKey()).append(":").append(entry.getValue()).append(SIGN_SEP);
           }

           // handle CanonicalizedResource
           stringToSign.append("/");
           if(this.isValid(bucketName)) {
               stringToSign.append(bucketName).append("/");
               if(this.isValid(objectName)) {
                   stringToSign.append(this.urlEncode(objectName));
               }
           }

           TreeMap<String, String> canonicalizedResource = new TreeMap<String, String>();
           for(Map.Entry<String, String> entry : queries.entrySet()) {
               key = entry.getKey();
               if(key == null) {
                   continue;
               }

               if(SUB_RESOURCES.contains(key)) {
                   canonicalizedResource.put(key, entry.getValue());
               }
           }

           if(canonicalizedResource.size() > 0) {
               stringToSign.append("?");
               for(Map.Entry<String, String> entry : canonicalizedResource.entrySet()) {
                   stringToSign.append(entry.getKey());
                   if(this.isValid(entry.getValue())) {
                       stringToSign.append("=").append(entry.getValue());
                   }
               }
           }

   //     System.out.println(String.format("StringToSign:%s%s", SIGN_SEP, stringToSign.toString()));

           return stringToSign.toString();
       }

       public String headerSignature(String httpMethod, Map<String, String[]> headers, Map<String, String> queries,
               String bucketName, String objectName) throws Exception {

           //1. stringToSign
           String stringToSign = this.stringToSign(httpMethod, headers, queries, bucketName, objectName);

           //2. signature
           return String.format("OBS %s:%s", this.ak, this.hamcSha1(stringToSign));
       }


       public String querySignature(String httpMethod, Map<String, String[]> headers, Map<String, String> queries,
               String bucketName, String objectName, long expires) throws Exception {
           if(headers.containsKey("x-obs-date")) {
               headers.put("x-obs-date", new String[] {String.valueOf(expires)});
           }else {
               headers.put("date", new String[] {String.valueOf(expires)});
           }
           //1. stringToSign
           String stringToSign = this.stringToSign(httpMethod, headers, queries, bucketName, objectName);

           //2. signature
           return this.urlEncode(this.hamcSha1(stringToSign));
       }

       public static void main(String[] args) throws Exception {

           SignDemo demo = new SignDemo();
           demo.ak = "<your-access-key-id>";
           demo.sk = "<your-secret-key-id>";

           String bucketName = "bucket-test";
           String objectName = "hello.jpg";
           Map<String, String[]> headers = new HashMap<String, String[]>();
           headers.put("date", new String[] {"Sat, 12 Oct 2015 08:12:38 GMT"});
           headers.put("x-obs-acl", new String[] {"private"});
           Map<String, String> queries = new HashMap<String, String>();
           queries.put("acl", null);

           System.out.println(demo.headerSignature("PUT", headers, queries, bucketName, objectName));
       }

   }

The calculation result of the signature is as follows (it varies with the execution time): YdH8ffpcbS6YpeOMcEZfn0wE90c=

Signature Algorithm in Python
-----------------------------

::

   import sys
   import os
   import hashlib
   import hmac
   import binascii
   from datetime import datetime
   IS_PYTHON2 = sys.version_info.major == 2 or sys.version < '3'
   """Hard-coded or plaintext SecretAccessKeyID is risky. For security purposes, encrypt your access key and store it in the configuration file or environment variables. In this example, SecretAccessKeyID is stored in the environment variables for identity authentication. Before running the code in this example, configure environment variable SECRET_ACCESS_KEY_ID."""
   yourSecretAccessKeyID = os.environ.get('SECRET_ACCESS_KEY_ID')
   httpMethod = "PUT"
   contentType = "application/xml"
   # "date" is the time when the request was actually generated
   date = datetime.utcnow().strftime('%a, %d %b %Y %H:%M:%S GMT')
   canonicalizedHeaders = "x-obs-acl:private\n"
   CanonicalizedResource = "/newfilesystem2"
   canonical_string = httpMethod + "\n" + "\n" + contentType + "\n" + date + "\n" + canonicalizedHeaders + CanonicalizedResource
   if IS_PYTHON2:
        hashed = hmac.new(yourSecretAccessKeyID, canonical_string, hashlib.sha1)
        encode_canonical = binascii.b2a_base64(hashed.digest())[:-1]
   else:
        hashed = hmac.new(yourSecretAccessKeyID.encode('UTF-8'), canonical_string.encode('UTF-8'),hashlib.sha1)
        encode_canonical = binascii.b2a_base64(hashed.digest())[:-1].decode('UTF-8')
   print encode_canonical

The calculation result of the signature is as follows (it varies with the execution time): YdH8ffpcbS6YpeOMcEZfn0wE90c=
