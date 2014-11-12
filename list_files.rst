=============
List Files
=============

+---------------+------------------------+
| **Resource:** | .. container:: notrans |
|               |                        |
|               |    /api/files          |
+---------------+------------------------+
| **Method:**   | .. container:: notrans |
|               |                        |
|               |    GET                 |
+---------------+------------------------+

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
| .. container:: notrans  | Container               | Container of File          |
|                         |                         |                            |
|    File                 |                         | information                |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | Integer                 | Internal onDemand ID       |
|                         |                         |                            |
|    File                 |                         | for the file asset.        |
|                         |                         |                            |
|      .AssetID           |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | The current state in the   |
|                         |                         |                            |
|    File                 |                         | onDemand File Lifecycle    |
|                         |                         |                            |
|      .Status            |                         | See :doc:`add_file`.       |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | Integer                 | Internal onDemand ID       |
|                         |                         |                            |
|    File                 |                         | of the project that this   |
|                         |                         |                            |
|      .ProjectID         |                         | asset has been associated  |
|                         |                         |                            |
|                         |                         | with. If no project has    |
|                         |                         |                            |
|                         |                         | been associated, this      |
|                         |                         |                            |
|                         |                         | element will be empty.     |
|                         |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | Original name of the file. |
|                         |                         |                            |
|    File                 |                         |                            |
|                         |                         |                            |
|      .Name              |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | URL to download the        |
|                         |                         |                            |
|    File                 |                         | file.                      |
|                         |                         |                            |
|      .URL               |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | See Language Code          |
|                         |                         |                            |
|    File                 |                         | in the glossary.           |
|                         |                         |                            |
|      .SourceLanguage    |                         |                            |
|                         |                         |                            |
|      .LanguageCode      |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | Integer                 | String representing the    |
|                         |                         |                            |
|    File                 |                         | date/time in the ISO       |
|                         |                         |                            |
|      .UploadDate        |                         | 8601 format. that the      |
|                         |                         |                            |
|                         |                         | project was created in     |
|                         |                         |                            |
|                         |                         | UTC.                       |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | Container               | Container containing       |
|                         |                         |                            |
|    File                 |                         | target languages that      |
|                         |                         |                            |
|      .TargetLanguages   |                         | the file was set to be     |
|                         |                         |                            |
|                         |                         | translated into. If the    |
|                         |                         |                            |
|                         |                         | file has not been          |
|                         |                         |                            |
|                         |                         | associated with a project  |
|                         |                         |                            |
|                         |                         | yet, this element will be  |
|                         |                         |                            |
|                         |                         |                            |
|                         |                         | empty.                     |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | See LanguageCode in        |
|                         |                         |                            |
|    File                 |                         | glossary                   |
|                         |                         |                            |
|      .TargetLanguages   |                         |                            |
|                         |                         |                            |
|      .TargetLanguage    |                         |                            |
|                         |                         |                            |
|      .LanguageCode      |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | The status of the          |
|                         |                         |                            |
|    File                 |                         | translation                |
|                         |                         |                            |
|      .TargetLanguages   |                         |                            |
|                         |                         |                            |
|      .TargetLanguage    |                         |                            |
|                         |                         |                            |
|      .Status            |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | URL to retrieve the        |
|                         |                         |                            |
|    File                 |                         | project information.       |
|                         |                         |                            |
|      .TargetLanguages   |                         |                            |
|                         |                         |                            |
|      .TargetLanguage    |                         |                            |
|                         |                         |                            |
|      .ProjectURL        |                         |                            |
+-------------------------+-------------------------+----------------------------+
| .. container:: notrans  | String                  | URL to download the        |
|                         |                         |                            |
|    File                 |                         | translated file.  See      |
|                         |                         |                            |
|      .TargetLanguages   |                         | :doc:`get_file_translation`|
|                         |                         |                            |
|      .TargetLanguage    |                         |                            |
|                         |                         |                            |
|      .DownloadURL       |                         |                            |
+-------------------------+-------------------------+----------------------------+

  

Response Example
================

The below example shows files in different states.

::

    <Files>
        <File>
            <AssetID>9000</AssetID>
            <Status>New</Status>
            <URL>http://</URL>
            <Name>1.txt</Name>
            <SourceLanguage>
                <LanguageCode>en-gb</LanguageCode>
            </SourceLanguage>
            <UploadDate>2014-01-25T10:32:02Z</UploadDate>
        </File>
        <File>
            <AssetID>9900</AssetID>
            <Status>Analyzed</Status>
            <URL>http://</URL>
            <Name>1.txt</Name>
            <SourceLanguage>
                <LanguageCode>en-gb</LanguageCode>
            </SourceLanguage>
            <UploadDate>2014-01-25T10:32:02Z</UploadDate>
        </File>
        <File>
            <AssetID>9901</AssetID>
            <Status>Analysis Failed</Status>
            <URL>http://</URL>
            <Name>1.txt</Name>
            <SourceLanguage>
                <LanguageCode>en-gb</LanguageCode>
            </SourceLanguage>
            <UploadDate>2014-01-25T10:32:02Z</UploadDate>
        </File>
        <File>
            <AssetID>9910</AssetID>
            <Status>In Translation</Status>
            <ProjectID>1234</ProjectID>
            <URL>http://</URL>
            <Name>foo.txt</Name>
            <SourceLanguage>
                <LanguageCode>en-gb</LanguageCode>
            </SourceLanguage>
            <UploadDate>2014-01-25T10:32:02Z</UploadDate>
            <TargetLanguages>
                <TargetLanguage>
                    <LanguageCode>de-de</LanguageCode>
                    <Status>Started</Status>
                    <ProjectURL>https://</ProjectURL>
                </TargetLanguage>
                <TargetLanguage>
                    <LanguageCode>fr-fr</LanguageCode>
                    <Status>Started</Status>
                    <ProjectURL>https://</ProjectURL>
                </TargetLanguage>
            </TargetLanguages>
        </File>
        <File>
            <AssetID>9999</AssetID>
            <Status>Translated</Status>
            <ProjectID>1234</ProjectID>
            <URL>http://</URL>
            <Name>foo.txt</Name>
            <SourceLanguage>
                <LanguageCode>en-gb</LanguageCode>
            </SourceLanguage>
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
        </File>
    <Files>