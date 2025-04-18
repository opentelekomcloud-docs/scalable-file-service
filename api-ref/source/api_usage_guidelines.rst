:original_name: sfs_02_0001.html

.. _sfs_02_0001:

API Usage Guidelines
====================

Public cloud APIs comply with the RESTful API design principles. REST-based web services are organized into resources. Each resource is identified by one or more Uniform Resource Identifiers (URIs). An application accesses a resource based on the resource's Unified Resource Locator (URL). A URL is usually in the following format: https://*Endpoint/uri*. In the URL, **uri** indicates the resource path, that is, the API access path.

Public cloud APIs use HTTPS as the transmission protocol. Requests/Responses are transmitted by using JSON messages, with media type represented by **Application/json**.

For details about how to use APIs, see `API Usage Guidelines <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328001.html?tag=API%20Documents>`__.

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions.

.. table:: **Table 1** SFS endpoint information

   +------------------------------------+--------+-----------------------------------+----------+
   | Service Name                       | Region | URL                               | Protocol |
   +====================================+========+===================================+==========+
   | Scalable File Service Turbo        | eu-de  | sfs-turbo.eu-de.otc.t-systems.com | HTTPS    |
   +------------------------------------+--------+-----------------------------------+----------+
   |                                    | eu-nl  | sfs-turbo.eu-nl.otc.t-systems.com | HTTPS    |
   +------------------------------------+--------+-----------------------------------+----------+
   | Scalable File Service              | eu-de  | sfs.eu-de.otc.t-systems.com       | HTTPS    |
   +------------------------------------+--------+-----------------------------------+----------+
   | General Purpose File System (BETA) | eu-de  | sfs3.eu-de.otc.t-systems.com      | HTTPS    |
   +------------------------------------+--------+-----------------------------------+----------+
