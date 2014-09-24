===================
Add File
===================

+-----------------+--------------------------------------------------+
| **Resource:**   | .. container:: notrans                           |
|                 |                                                  |
|                 |    /api/files/add/<<language_code>>/<<filename>> |
+-----------------+--------------------------------------------------+
| **Method:**     | .. container:: notrans                           |
|                 |                                                  |
|                 |    POST                                          |
+-----------------+--------------------------------------------------+

This interface adds a file to the system. 

The URL for this method includes two parameters.  


- language_code is a locale code like "en-gb" where "en" the 2 character ISO language code for English and "gb" is the 2 character ISO country code for Great Britain.
- filename is the original name of the file.  It needs to be url encoded.

Files are then used to generate quotes.  If a file is not used in a quote
within 1 hour of it being uploaded it will be deleted from the system.  Lionbridge onDemand has a general retention 
policy of 60 days for all customer content.

Files can only be associated with one project. If you need to translate a file into additional languages, you can upload it again
and create a new project out of it.

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


Content-Type Header
===================
To ensure proper file handling, send a content-type header that is consistent with the file you are uploading.  

We currently support the following file types:

+-------------------------+-----------+--------------------------------------------------------------------------------+
| File Type               | Extension | Mime Type                                                                      |
+=========================+===========+================================================================================+
| Comma separated files   | csv       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/csv                                                                    |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Microsoft Word          | docx      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/vnd.openxmlformats-officedocument.wordprocessingml.document     |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Flash Video             | flv       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    video/x-flv                                                                 |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| HTML                    | htm/html  | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/html                                                                   |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| InDesign Export         | idml      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/xml                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| INI                     | ini       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| InDesign Exchange       | inx       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/xml                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| JSON                    | json      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/json                                                            |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| M4V                     | m4v       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    video/x-m4v                                                                 |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| FrameMaker Interchange  | mif       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/vnd.mif                                                         |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Apple QuickTime         | mov       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    video/quicktime                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| MP4                     | mp4       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    video/mp4                                                                   |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Portable Document Format| pdf       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/pdf                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| GetText                 | po        | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Microsoft PowerPoint    | pptx      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/vnd.openxmlformats-officedocument.presentationml.presentation   |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Properties              | properties| .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Photoshop               | psd       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    image/vnd.adobe.photoshop                                                   |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| RESJSON                 | resjson   | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/json                                                            |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| RESW                    | resw      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/xml                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| RESX                    | resx      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/xml                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Rich Text Format        | rtf       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/rtf                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| SubRip                  | srt       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Strings                 | strings   | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Text                    | txt       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| WebVTT                  | vtt       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/plain                                                                  |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Microsoft Media Video   | wmv       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    video/x-ms-wmv                                                              |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| XLIFF                   | xlf/xliff | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/xml                                                             |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| Microsoft Excel         | xlsx      | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/vnd.openxmlformats-officedocument.spreadsheetml.sheet           |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| XML                     | XML       | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    application/xml, text/xml                                                   |
+-------------------------+-----------+--------------------------------------------------------------------------------+
| YAML                    | yml/yaml  | .. container:: notrans                                                         |
|                         |           |	                                                                               |
|                         |           |    text/yaml                                                                   |
+-------------------------+-----------+--------------------------------------------------------------------------------+


Request Body
============

The request body should contain the contents of the file. 


Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Created                 | 201                     | The project was created |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     | This is probably        |
|                         |                         |                         |
|                         |                         | because of an invalid   |
|                         |                         |                         |
|                         |                         | file type or a content  |
|                         |                         |                         |
|                         |                         | type that does not      |
|                         |                         |                         |
|                         |                         | match with the extension|
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
