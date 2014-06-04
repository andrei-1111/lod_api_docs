=============
List Files
=============

=============  ======================
**Resource:**  /api/files
**Method:**    GET
=============  ======================

Returns a list of all files submitted by user.

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

Response Body
=============

The response body includes a list of file assets.


+-------------------------+-------------------------+----------------------------+
| Property                | Type                    | Comments                   |
+=========================+=========================+============================+
| File                    | Container               | Container of File          |
|                         |                         |                            |
|                         |                         | information                |
+-------------------------+-------------------------+----------------------------+
| File                    | Integer                 | Internal onDemand ID       |
|                         |                         |                            |
| .AssetID                |                         | for the file asset.        |
|                         |                         |                            |
+-------------------------+-------------------------+----------------------------+
| File                    | String                  | Original name of the file. |
|                         |                         |                            |
| .Name                   |                         |                            |
|                         |                         |                            |
|                         |                         |                            |
+-------------------------+-------------------------+----------------------------+
| File                    | String                  | URL to download the        |
|                         |                         |                            |
| .URL                    |                         | file.                      |
|                         |                         |                            |
+-------------------------+-------------------------+----------------------------+
| File                    | Integer                 | String representing the    |
|                         |                         |                            |
| .UploadDate             |                         | date/time in the ISO       |
|                         |                         |                            |
|                         |                         | 8601 format. that the      |
|                         |                         |                            |
|                         |                         | project was created in     |
|                         |                         |                            |
|                         |                         | UTC.                       |
+-------------------------+-------------------------+----------------------------+
| File                    | Container               | Container containing       |
|                         |                         |                            |
| .TargetLanguages        |                         | target languages that      |
|                         |                         |                            |
|                         |                         | the file was set to be     |
|                         |                         |                            |
|                         |                         | translated into.           |
+-------------------------+-------------------------+----------------------------+
| File                    | String                  | See LanguageCode in        |
|                         |                         |                            |
| .TargetLanguages        |                         | glossary                   |
|                         |                         |                            |
| .TargetLanguage         |                         |                            |
|                         |                         |                            |
| .LanguageCode           |                         |                            |
|                         |                         |                            |
+-------------------------+-------------------------+----------------------------+
| File                    | String                  | The status of the          |
|                         |                         |                            |
| .TargetLanguages        |                         | translation                |
|                         |                         |                            |
| .TargetLanguage         |                         |                            |
|                         |                         |                            |
| .Status                 |                         |                            |
+-------------------------+-------------------------+----------------------------+
| File                    | String                  | URL to retrieve the        |
|                         |                         |                            |
| .TargetLanguages        |                         | project information.       |
|                         |                         |                            |
| .TargetLanguage         |                         |                            |
|                         |                         |                            |
| .ProjectURL             |                         |                            |
+-------------------------+-------------------------+----------------------------+
| File                    | String                  | URL to download the        |
|                         |                         |                            |
| .TargetLanguages        |                         | translated file.  See      |
|                         |                         |                            |
| .TargetLanguage         |                         | :doc:`get_file_translation`|
|                         |                         |                            |
| .DownloadURL            |                         |                            |
+-------------------------+-------------------------+----------------------------+

  

Response Example
================

::

    <Files>
        <Files>
            <AssetID>9999</AssetID>
            <ProjectID>1234</ProjectID>
            <URL>http://</URL>
            <Name>foo.txt</Name>
            <UploadDate>2014-01-25T10:32:02Z</UploadDate>
            <TargetLanguages>
                <TargetLanguage>
                    <LanguageCode>de-de</LanguageCode>
                    <Status>Complete</Status>
                    <ProjectURL>https://</ProjectURL>
                    <DownloadURL>https://ondemand…</DownloadURL>
                </TargetLanguage>
                <TargetLanguage>
                    <LanguageCode>fr-fr</LanguageCode>
                    <Status>Complete</Status>
                    <ProjectURL>https://</ProjectURL>
                    <DownloadURL>https://liondemand.com<DownloadURL>
                </TargetLanguage>
            </TargetLanguages>
        </Files>
    <Files>