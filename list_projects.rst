=============
List Projects
=============

=============  ======================
**Resource:**  /api/projects
**Method:**    GET
=============  ======================

Returns information about the merchant’s account

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

The response body lists all of the projects associated with the API
credentials.

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| Project                 | Integer                 | The onDemand ID of the  |
|                         |                         |                         |
| .ProjectID              |                         | Project                 |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Project                 | String                  | The URL to retrieve the |
|                         |                         |                         |
| .URL                    |                         | project. See            |
|                         |                         |                         |
|                         |                         | GetProject.             |
+-------------------------+-------------------------+-------------------------+
| Project                 | String                  | The status of the       |
|                         |                         |                         |
| .Status                 |                         | Project                 |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Project                 | Integer                 | The onDemand service    |
|                         |                         |                         |
| .ServiceID              |                         | configuration used for  |
|                         |                         |                         |
|                         |                         | the project             |
+-------------------------+-------------------------+-------------------------+
| Project                 | Decimal                 | Price charged for the   |
|                         |                         |                         |
| .TotalPrice             |                         | project                 |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Project                 | String                  | The currency that the   |
|                         |                         |                         |
| .Currency               |                         | project was paid in.    |
|                         |                         |                         |
|                         |                         |  See glossary for list  |
|                         |                         |                         |
|                         |                         | of valid currencies.    |
+-------------------------+-------------------------+-------------------------+
| Project                 | DateTime                | String representing     |
|                         |                         |                         |
| .CreationDate           |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the Item was      |
|                         |                         |                         |
|                         |                         | added to onDemand.      |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Project                 | DateTime                | String representing     |
|                         |                         |                         |
| .DueDate                |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the translation   |
|                         |                         |                         |
|                         |                         | of the item is          |
|                         |                         |                         |
|                         |                         | scheduled to be         |
|                         |                         |                         |
|                         |                         | completed.              |
+-------------------------+-------------------------+-------------------------+
| Project                 | DateTime                | String representing     |
|                         |                         |                         |
| .CompletionDate         |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the translation   |
|                         |                         |                         |
|                         |                         | of the item was         |
|                         |                         |                         |
|                         |                         | completed.              |
+-------------------------+-------------------------+-------------------------+
| SourceLanguage.Language | String                  | See LanguageCode in     |
|                         |                         |                         |
| Code                    |                         | glossary                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Container containing    |
|                         |                         |                         |
|                         |                         | target languages.       |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | String                  | See LanguageCode in     |
|                         |                         |                         |
| .TargetLanguages        |                         | glossary                |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
  

Response Example
================

::

    <Projects>
        <Project>
            <ProjectID>10001</ProjectID>
                <URL>https://ondemand...</URL>
                <Status>Complete</Status>
                <ServiceID>14</ServiceID>
                <TotalPrice>100.00</TotalPrice>
                <Currency>USD</Currency>
                <CreationDate>2014-01-25T10:32:02Z</CreationDate>
                <DueDate>2014-01-25T10:32:02Z</DueDate>
                <CompletionDate>2014-01-25T10:32:02Z</CompletionDate>
                <SourceLanguage>
                    <LanguageCode>en-gb</LanguageCode>
                </SourceLanguage>
                <TargetLanguages>
                    <TargetLanguage>
                        <LanguageCode>fr-fr</LanguageCode>
                    </TargetLanguage>
                    <TargetLanguage>
                        <LanguageCode>it-it</LanguageCode>
                    </TargetLanguage>
                </TargetLanguages>
        </Project>
    </Projects>