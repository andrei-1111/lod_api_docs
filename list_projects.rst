=============
List Projects
=============

+---------------+------------------------+
| **Resource:** | .. container:: notrans |
|               |                        |
|               |    /api/projects       |
+---------------+------------------------+
| **Method:**   | .. container:: notrans |
|               |                        |
|               |    GET                 |
+---------------+------------------------+

Returns a list of all a user's projects.

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
| .. container:: notrans  | Integer                 | The onDemand ID of the  |
|                         |                         |                         |
|    Project              |                         | Project                 |
|                         |                         |                         |
|      .ProjectID         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The URL to retrieve the |
|                         |                         |                         |
|    Project              |                         | project. See            |
|                         |                         |                         |
|      .URL               |                         | GetProject.             |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The name of the project |
|                         |                         |                         |
|    Project              |                         | Either provided or      |
|                         |                         |                         |
|      .ProjectName       |                         | system generated.       |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The status of the       |
|                         |                         |                         |
|    Project              |                         | Project                 |
|                         |                         |                         |
|      .Status            |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | The onDemand service    |
|                         |                         |                         |
|    Project              |                         | configuration used for  |
|                         |                         |                         |
|      .ServiceID         |                         | the project             |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | Price charged for the   |
|                         |                         |                         |
|    Project              |                         | project                 |
|                         |                         |                         |
|      .TotalPrice        |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The currency that the   |
|                         |                         |                         |
|    Project              |                         | project was paid in.    |
|                         |                         |                         |
|      .Currency          |                         |  See glossary for list  |
|                         |                         |                         |
|                         |                         | of valid currencies.    |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | DateTime                | String representing     |
|                         |                         |                         |
|    Project              |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|      .CreationDate      |                         |  that the Item was      |
|                         |                         |                         |
|                         |                         | added to onDemand.      |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | DateTime                | String representing     |
|                         |                         |                         |
|    Project              |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|      .DueDate           |                         |  that the translation   |
|                         |                         |                         |
|                         |                         | of the item is          |
|                         |                         |                         |
|                         |                         | scheduled to be         |
|                         |                         |                         |
|                         |                         | completed.              |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | DateTime                | String representing     |
|                         |                         |                         |
|    Project              |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|      .CompletionDate    |                         |  that the translation   |
|                         |                         |                         |
|                         |                         | of the item was         |
|                         |                         |                         |
|                         |                         | completed.              |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    SourceLanguage       |                         | glossary                |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container containing    |
|                         |                         |                         |
|    TargetLanguages      |                         | target languages.       |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    TargetLanguages      |                         | glossary                |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
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