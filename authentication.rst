==============
Authentication
==============

Every request to the API needs to be authenticated using a signature in the HTTP headers.  
A good place to start when building out your request signing logic is the :doc:`list_services` API. 

There is a clear example written in PHP `here <https://bitbucket.org/sggottlieb/liox_ondemand_php_client/src/>`_. See listServices.php.



Keys
----

API accounts will be given a key pair consisting of an Access Key ID
(like ‘qzwBzqCiMsuHoUrZEcLq’) and a Secret Access Key (like
‘znkcyBjEWKQFIELAkotspHDoJbwHJyRPXChFYWDn’).  These keys will be used to
sign every request.  Keys are tied to a merchant account.

Headers
-------

The API requires that the client send the following headers. All
required x-lod-\* headers are used to compute authorization.

-  authorization: contains authorization components as described below
-  accept: in this version we will only be supporting XML.  Anything
   other than “text/xml” will result in a Bad Request error.
-  x-lod-timestamp: UNIX timestamp
-  x-lod-version: version of the API. We will use date strings to label
   versions. For example: 2014-03-18
-  Content-Type should be "text/xml".  Often this will default on GET requests.
   Depending on what libraries you use, you might need to explicitly set Content-Type
   on POSTs or force it by submitting an empty string in the body if no body is required.

Authorization Header
--------------------

An example POST against the resource /api/project might have an
authorization header like

 
::
    
    Authorization: LOD1-BASE64-SHA256
    KeyID=ChpmKHmUMvtegpEcvFaQ,Signature=cbRgimKByXtv7k+3eI01lcR2VQzSu6vltdB/bSAMgiM=,SignedHeaders=x-lod-timestamp;x-lod-version;accept

Note that there is space between the first two components,
LOD1-BASE64-SHA256 and KeyID, and that the subsequent components, KeyID,
Signature, and SignedHeaders are separated by a comma.

The following table describes the various components of the
Authorization header value.


+--------------------------------------+--------------------------------------+
| Component                            | Description                          |
+======================================+======================================+
| .. container:: notrans               | The algorithm that was used to       |
|                                      |                                      |
|    LOD1-BASE64-SHA256                | calculate the signature.             |
|                                      |                                      |
|                                      | The string specifies LOD Signature   |
|                                      |                                      |
|                                      | Version 1 (LOD1) and the signing     |
|                                      |                                      |
|                                      | algorithm (BASE64-SHA256).           |
|                                      |                                      |
+--------------------------------------+--------------------------------------+
| .. container:: notrans               | A valid Access Key ID.               |
|                                      |                                      |
|    KeyID                             |                                      |
+--------------------------------------+--------------------------------------+
| .. container:: notrans               | A signature in the form of           |
|                                      |                                      |
|    Signature                         | BASE64(SHA256(METHOD:RESOURCE:secret |
|                                      |                                      |
|                                      | key:x-lod-header-a:x-lod-header-b))  |
+--------------------------------------+--------------------------------------+
| .. container:: notrans               | A semicolon-separated list of        |
|                                      |                                      |
|    SignedHeaders                     | request headers used to compute      |
|                                      |                                      |
|                                      | Signature. The list includes header  |
|                                      |                                      |
|                                      | names only. The required x-lod-\*    |
|                                      |                                      |
|                                      | headers must be first and in         |
|                                      |                                      |
|                                      | alphabetical order. For example,     |
|                                      |                                      |
|                                      | x-lod-timestamp;x-lod-version;accept |
+--------------------------------------+--------------------------------------+

Example
-------

The best place to start when learning how to develop a valid request signature is the 
:doc:`list_services` API.  In this case, the string to encrypt for the signature is:

::

    GET:/api/services:AAA...AAA:2014-02-21T07:49:24.655024:2014-02-28:text/xml

Where:

- **GET** is the HTTP method you used
- **/api/services** is the resource you are calling
- **AAA...AAA** is your secret key
- **2014-02-21T17:49:24.655024** is the current time stamp. This needs to be the same as x-lod-timestamp. Note, you must use a 24 hour clock.
- **2014-02-28** is the version of the API you are using. This needs to be the same as x-lod-version.
- **text/xml** is what you passed in the accept header