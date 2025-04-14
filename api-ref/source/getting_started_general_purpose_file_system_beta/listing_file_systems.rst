:original_name: sfs_02_0109.html

.. _sfs_02_0109:

Listing File Systems
====================

Scenarios
---------

If you want to view information about all file systems created by yourself, you can call the API for listing file systems.

The following describes how to call the API for :ref:`Listing File Systems <sfs_02_0114>`. For details, see :ref:`Getting Started (General Purpose File System) (BETA) <sfs_02_0107>`.

Prerequisites
-------------

-  You have obtained the AK and SK. For details, see :ref:`Obtaining Access Keys (AK/SK) <sfs_02_0120>`.
-  You have specified the region where you want to list file systems and obtained the endpoint required for API calls. For details, see `Regions and Endpoints <https://docs.otc.t-systems.com/regions-and-endpoints/index.html>`__.

Listing File Systems in the a1 Region
-------------------------------------

In this example, an Apache HttpClient is used.

::

   package com.sfsclient;

   import java.io.*;
   import java.net.HttpURLConnection;
   import java.net.URL;
   import java.util.List;
   import java.util.Map;

   public class TestMain {
       //Obtain an AK/SK pair using environment variables or import the AK/SK pair in other ways. Using hard coding may result in leakage.
       //Obtain an AK/SK pair on the management console.
       String accessKey = System.getenv("YOUR_SDK_AK");
       String securityKey = System.getenv("YOUR_SDK_SK");
       String endpoint = "sfs3.a1.region.com"; // The access address of General Purpose File System

       public static void main(String[] str) {
           createFileSystem();

       }
       private static void listFileSystem() {
           String httpMethod = "GET";
           String date = DateUtils.formatDate(System.currentTimeMillis());

           /**Calculate the signature based on the request.**/
           String contentMD5 = "";
           String contentType = "";
           String canonicalizedHeaders = "x-obs-bucket-type:SFS";
           String canonicalizedResource = "/" ;

           // Content-MD5 and Content-Type fields do not contain line breaks. The data format is RFC 1123, which is the same as the time in the request.
           String stringToSign = httpMethod + "\n" +
                   contentMD5 + "\n" +
                   contentType + "\n" +
                   date + "\n" +
                   canonicalizedHeaders  + "\n" + canonicalizedResource;

           System.out.printf("StringToSign:\n[%s]\n\n", stringToSign);

           HttpURLConnection conn = null;

           try {
               String signature = Signature.signWithHmacSha1(securityKey, stringToSign);
               String authorization= "OBS " + accessKey + ":" + signature;
               System.out.printf("authorization:%s\n\n", authorization);

               // Create an HTTP request.
               URL url = new URL("http://" + endpoint);
               conn = (HttpURLConnection) url.openConnection();

               // Add a signature header.
               conn.setRequestMethod(httpMethod);
               conn.setRequestProperty("Date", date);
               conn.setRequestProperty("Content-Type", contentType);
               conn.setRequestProperty("x-obs-bucket-type", "SFS");
               conn.setRequestProperty("Authorization", authorization);
               conn.setDoOutput(true);

               String status = conn.getHeaderField(null);
               System.out.println(status);

               // Output the response message.
               Map<String, List<String>> headers = conn.getHeaderFields();
               for (Map.Entry<String, List<String>> entry : headers.entrySet()) {
                   String key = entry.getKey();
                   List<String> values = entry.getValue();
                   if (key != null) {
                       for (String value : values) {
                           System.out.println(key + ": " + value);
                       }
                   }
               }
               // Process the returned content.
               int statusCode = conn.getResponseCode();
               if (statusCode == HttpURLConnection.HTTP_OK) {
                   InputStream responseStream = conn.getInputStream();
                   BufferedReader reader = new BufferedReader(new InputStreamReader(responseStream));

                   StringBuilder responseBody = new StringBuilder();
                   String line;
                   while ((line = reader.readLine()) != null) {
                       responseBody.append(line);
                   }
                   reader.close();

                   System.out.println("responseBody: " + responseBody);
               } else {
                   System.out.println("Error: " + statusCode);
               }
           } catch (IOException e) {
               e.printStackTrace();
           } finally {
               if (conn != null){
                   conn.disconnect();
               }
           }
       }
   }

The format of the **Date** header field **DateUtils** is as follows:

::

   package com.sfsclient;

   import java.text.DateFormat;
   import java.text.SimpleDateFormat;
   import java.util.Locale;
   import java.util.TimeZone;

   public class DateUtils {

       public static String formatDate(long time)
       {
           DateFormat serverDateFormat = new SimpleDateFormat("EEE, dd MMM yyyy HH:mm:ss z", Locale.ENGLISH);
           serverDateFormat.setTimeZone(TimeZone.getTimeZone("GMT"));
           return serverDateFormat.format(time);
       }
   }

The method of calculating the signature character string is as follows:

::

   package com.sfsclient;

   import javax.crypto.Mac;
   import javax.crypto.spec.SecretKeySpec;
   import java.io.UnsupportedEncodingException;
   import java.security.NoSuchAlgorithmException;
   import java.security.InvalidKeyException;
   import java.util.Base64;

   public class Signature {
       public static String signWithHmacSha1(String sk, String canonicalString) throws UnsupportedEncodingException {

           try {
               SecretKeySpec signingKey = new SecretKeySpec(sk.getBytes("UTF-8"), "HmacSHA1");
               Mac mac = Mac.getInstance("HmacSHA1");
               mac.init(signingKey);
               return Base64.getEncoder().encodeToString(mac.doFinal(canonicalString.getBytes("UTF-8")));
           } catch (NoSuchAlgorithmException | InvalidKeyException | UnsupportedEncodingException e) {
               e.printStackTrace();
           }
           return null;
       }
   }
