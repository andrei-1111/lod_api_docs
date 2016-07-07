=================
Get File Details
=================

+---------------+------------------------------------+
| **Resource:** | .. container:: notrans             |
|               |                                    |
|               |    /api/files/<<asset id>>/details |
+---------------+------------------------------------+
| **Method:**   | .. container:: notrans             |
|               |                                    |
|               |    GET                             |
+---------------+------------------------------------+


Returns details about a file

Arguments
=========

- **Asset ID:** The onDemand Asset ID.  You will receive this ID from :doc:`add_file` 


Return Codes
============

+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Success                 | 200                     | Successful request      |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     |                         |
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
| Not Found               | 404                     | The URL does not relate |
|                         |                         |                         |
|                         |                         | to a product that the   |
|                         |                         |                         |
|                         |                         | user owns.              |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body shows information about the file.


+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | String                  | The onDemand ID of the  |
|                         |                         |                         |
|    AssetID              |                         | asset                   |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The name of the file    |
|                         |                         |                         |
|    Name                 |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The language of the file|
|                         |                         |                         |
|    SourceLanguage       |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | If the file is          |
|                         |                         |                         |
|    ProjectID            |                         | associated with a       |
|                         |                         |                         |
|                         |                         | project, this element   |
|                         |                         |                         |
|                         |                         | contains the ID.        |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  |                         | If the file is a target |
|                         |                         |                         |
|    AcceptedBy           |                         | file and has been       |
|                         |                         |                         |
|                         |                         | accepted, the user who  |
|                         |                         |                         |
|                         |                         | accepted it.            |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  |                         | If the file is a target |
|                         |                         |                         |
|    AcceptedDate         |                         | file and has been       |
|                         |                         |                         |
|                         |                         | accepted, the date it   |
|                         |                         |                         |
|                         |                         | was accepted.           |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  |                         | If the file is a target |
|                         |                         |                         |
|    AcceptedMethod       |                         | file and has been       |
|                         |                         |                         |
|                         |                         | accepted, the method of |
|                         |                         |                         |
|                         |                         | acceptance (implicit or |
|                         |                         |                         |
|                         |                         | explicit).              |
+-------------------------+-------------------------+-------------------------+



Response Example
================

::

    <File>
        <AssetID>123456</AssetID>
        <Name>Foo.txt</Name>
        <Status>Complete</Status>
        <AcceptedBy> Example &lt;user@example.com&gt; </AcceptedBy>
        <AcceptedDate>2016-03-15T04:00:00Z</AcceptedDate>
        <AcceptedMethod>implicit</AcceptedMethod>
        <SourceLanguage>
            <LanguageCode>en-gb</LanguageCode>
        </SourceLanguage>
        <ProjectID>10001</ProjectID>
    </File>
