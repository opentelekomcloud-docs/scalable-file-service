:original_name: sfs_01_1141.html

.. _sfs_01_1141:

How Do I Make the Most Out of My SFS Turbo File System?
=======================================================

An SFS Turbo file system provides multiple IP addresses that can be used for mounting. Each IP address can be used by multiple clients. For the specific IP addresses, see the **Alternative Shared Path** field on the file system details page on the console.

If the NFS protocol is used to access a file system, each client can only establish the network connection with one server. If you mount the file system using domain name, a random domain name server IP address is assigned. This may result in uneven distribution of network connections between clients and servers, and the distributed cluster capability of the servers cannot be fully used.

When there are not too many clients and you want to maximize the file system performance, you can use different IP addresses when mounting the file system on different clients. In this way, the network connections between clients and servers are more evenly distributed, server resources are used more efficiently, and the file system performance can be fully used.
