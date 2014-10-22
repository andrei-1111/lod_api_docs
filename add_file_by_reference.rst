======================
Add File By Reference
======================

+---------------+---------------------------------------------------------------+
| **Resource:** | .. container:: notrans                                        |
|               |                                                               |
|               |    /api/files/add_by_reference/<<language_code>>/<<filename>> |
+---------------+---------------------------------------------------------------+
| **Method:**   | .. container:: notrans                                        |
|               |                                                               |
|               |    POST                                                       |
+---------------+---------------------------------------------------------------+


This interface adds a file to onDemand by providing an external URL that onDemand can download from.  This is a good alternative to the :doc:`add_file` API for cases when the files are very large.

The URL for this method includes two parameters.  


- language_code is a locale code like "en-gb" where "en" the 2 character ISO language code for English and "gb" is the 2 character ISO country code for Great Britain.
- filename is the original name of the file.  It needs to be url encoded.

Files are then used to generate quotes.  If a file is not used in a quote
within 1 hour of it being uploaded it will be deleted from the system.  Lionbridge onDemand has a general retention 
policy of 60 days for all customer content.

Files can only be associated with one project. If you need to translate a file into additional languages, you can upload it again
and create a new project out of it.

When the onDemand receives a URL to retrieve, it does a quick check to see if the file is accessible.  For HTTP/HTTPS, onDemand will execute a 
HEAD request.  For FTP/SFTP, onDemand checks to see if the file exists in the parent directory stated in the path.  If onDemand believes that can download 
the file, it will create an asset and queue the file to be downloaded.


File Lifecycle
==============

.. file_lifecycle:

Files go through the following lifecycle.


+-------------------------+------------------------------------------------------+
| Status                  | Comments                                             |
+=========================+======================================================+
| Analyzing               | The file has been recently uploaded and onDemand     |
|                         |                                                      |
|                         | is still in the process of analyzing it.  At this    |
|                         |                                                      |
|                         | point, the file can be added to a quote but the      |
|                         |                                                      |
|                         | quote cannot be authorized yet.                      |
+-------------------------+------------------------------------------------------+
| Analyzed                | The file has been analyzed and onDemand can now      |
|                         |                                                      |
|                         | generate a price for it.  Quotes containing this     |
|                         |                                                      |
|                         | file can be authorized.                              |
|                         |                                                      |
+-------------------------+------------------------------------------------------+
| Analysis Failed         | onDemand could not parse the file and it cannot      |
|                         |                                                      |
|                         | be used in a project. Quotes containing this file    |
|                         |                                                      |
|                         | cannot be authorized.                                |
|                         |                                                      |
+-------------------------+------------------------------------------------------+
| In Translation          | This file has been added to a project and the project|
|                         |                                                      |
|                         | is being worked on.  This file cannot be added to    |
|                         |                                                      |
|                         | other quotes or projects.                            |
|                         |                                                      |
+-------------------------+------------------------------------------------------+
| Translated              | This file has been added to a project and the project|
|                         |                                                      |
|                         | is complete. This file cannot be added to other      |
|                         |                                                      |
|                         | quotes or projects.                                  |
|                         |                                                      |
+-------------------------+------------------------------------------------------+





Request Body
============

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | String                  | The full URL to the     |
|                         |                         |                         |
|    File                 |                         | file.  The URL must be  |
|                         |                         |                         |
|      .URL               |                         | publicly accessible.    |
|                         |                         |                         |
|                         |                         | It can use use http,    |
|                         |                         |                         |
|                         |                         | https, ftp, or ftps.    |
|                         |                         |                         |
|                         |                         | currencies. If the URL  |
|                         |                         |                         |
|                         |                         | requires authentication,|
|                         |                         |                         |
|                         |                         | credentials must be     |
|                         |                         |                         |
|                         |                         | passed in the URL.      |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+


Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Accepted                | 202                     | The URL looks good and  |
|                         |                         |                         |
|                         |                         | the file is queued for  |
|                         |                         |                         |
|                         |                         | retrieval.              |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     | This is probably        |
|                         |                         |                         |
|                         |                         | because the body of the |
|                         |                         |                         |
|                         |                         | request was malformed.  |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Unauthorized            | 401                     | The request did not     |
|                         |                         |                         |
|                         |                         | pass authentication or  |
|                         |                         |                         |
|                         |                         | the customer is not a   |
|                         |                         |                         |
|                         |                         | member of an enterprise |
|                         |                         |                         |
|                         |                         | site.                   |
+-------------------------+-------------------------+-------------------------+
| Conflict                | 409                     | The URL does not appear |
|                         |                         |                         |
|                         |                         | to be accessible to     |
|                         |                         |                         |
|                         |                         | onDemand.               |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+


Response Body
=============

The response body contains information about the credit balance request 
including a payment URL.  The user must follow this URL to a payment page.

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | Integer                 | ID of the uploaded file |
|                         |                         |                         |
|    AssetID              |                         | this ID will be used    |
|                         |                         |                         |
|                         |                         | when creating a quote   |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Name of the file passed |
|                         |                         |                         |
|    Name                 |                         |                         |
+-------------------------+-------------------------+-------------------------+


Response Example
================

::

    <File>
        <AssetID>1235</AssetID>
        <Name>foo.txt</Name>
    </File>


Errors
======
If Add File By Reference encountered an error, it will return an error element containing
a ReasonCode, SimpleMessage, and DetailedMessage elements. See :doc:`error_handling` for more 
information. Here are some common cases.

+-------------------------+-------------------------+-------------------------+
| ReasonCode              | SimpleMessage           | DetailedMessage         |
+=========================+=========================+=========================+
| 200                     | Miscellaneous error     | A miscellaneous or      |
|                         |                         |                         |
|                         |                         | unexpected error        |
|                         |                         |                         |
|                         |                         | has occured.            |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 501                     | There was a problem     | The target file could   |
|                         |                         |                         |
|                         | with the source content.| not be accessed. Verify |
|                         |                         |                         |
|                         |                         | that the URL is publicly|
|                         |                         |                         |
|                         |                         | accessible.             |
+-------------------------+-------------------------+-------------------------+

