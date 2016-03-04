==================
Reject Translation
==================

+---------------+-------------------------------------------------------------------+
| **Resource:** | .. container:: notrans                                            |
|               |                                                                   |
|               |   /api/files/<<asset id>>/<<language code>>/reject/               |
+---------------+-------------------------------------------------------------------+
| **Method:**   | .. container:: notrans                                            |
|               |                                                                   |
|               |    POST                                                           |
+---------------+-------------------------------------------------------------------+

This interface rejects a file translation. 


Request Body
============


+-------------------------+-------------------------+---------------------------------+
| Parameter               | Type                    | Comments                        |
+=========================+=========================+=================================+
| .. container:: notrans  | Container               | Contains information            |
|                         |                         |                                 |
|    RejectFile           |                         | on rejecting                    |
|                         |                         |                                 |
|                         |                         | translated file.                |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | Integer representing            |
|                         |                         |                                 |
|    RejectFile           |                         | the reason number of            |
|                         |                         |                                 |
|     .ReasonCode         |                         | rejecting translated file.      |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String (optional)       | String representing             |
|                         |                         |                                 |
|    RejectFile           |                         | the description of rejecting    |
|                         |                         |                                 |
|     .ReasonDescription  |                         | translated file.                |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+

Reject Translation Example
==========================

::

    <RejectFile>
        <ReasonCode>5000</ReasonCode>
        <ReasonDescription>
            Failed .po file validation

            Failure Details:

            <![CDATA[
              #: od_api/exceptions.py:239 od_api/serializers.py:454
              msgid "Asset is already in use."
              msgstr "
                     ^^^^^ expected end quote
            ]>

        </ReasonDescription>
    </RejectFile>


Response Body
=============

+---------------------------+-------------------------+---------------------------------+
| Parameter                 | Type                    | Comments                        |
+===========================+=========================+=================================+
| .. container:: notrans    | Integer                 | ID of the uploaded file         |
|                           |                         |                                 |
|    AssetID                |                         | this ID will be used            |
|                           |                         |                                 |
|                           |                         | when creating a quote           |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | Name of the file passed         |
|                           |                         |                                 |
|    Name                   |                         |                                 |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | The status of the file.         |
|                           |                         |                                 |
|    Status                 |                         | Rejected                        |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | See LanguageCode in             |
|                           |                         |                                 |
|    SourceLanguage         |                         | glossary                        |
|                           |                         |                                 |
|      .LanguageCode        |                         | The LanguageCode element        |
|                           |                         |                                 |
|                           |                         | will be empty if the            |
|                           |                         |                                 |
|                           |                         | client requested                |
|                           |                         |                                 |
|                           |                         | language detection and          |
|                           |                         |                                 |
|                           |                         | the file has not been           |
|                           |                         |                                 |
|                           |                         | analyzed yet or if              |
|                           |                         |                                 |
|                           |                         | language detection              |
|                           |                         |                                 |
|                           |                         | failed.                         |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | String represents               |
|                           |                         |                                 |
|    TargetLanguage         |                         | the rejected                    |
|                           |                         |                                 |
|      .LanguageCode        |                         | language code                   |
|                           |                         |                                 |
|                           |                         | See LanguageCode in             |
|                           |                         |                                 |
|                           |                         | glossary                        |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | Container               | Contains information            |
|                           |                         |                                 |
|    Rejection              |                         | on rejecting                    |
|                           |                         |                                 |
|                           |                         | translated file.                |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | Integer representing            |
|                           |                         |                                 |
|    Rejection              |                         | the reason number of            |
|                           |                         |                                 |
|      .ReasonCode          |                         | rejecting translated file.      |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String (optional)       | String representing             |
|                           |                         |                                 |
|    Rejection              |                         | the description of rejecting    |
|                           |                         |                                 |
|      .ReasonDescription   |                         | translated file.                |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | Container               | Contains information            |
|                           |                         |                                 |
|    Project                |                         | on project                      |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | Integer                 | onDemand ID of the              |
|                           |                         |                                 |
|    Project                |                         | project                         |
|                           |                         |                                 |
|      .ProjectID           |                         |                                 |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | A URL that can be               |
|                           |                         |                                 |
|    Project                |                         | checked for the status          |
|                           |                         |                                 |
|      .URL                 |                         | of the project.                 |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | Status of the project           |
|                           |                         |                                 | 
|    Project                |                         |                                 |
|                           |                         |                                 |
|      .Status              |                         |                                 | 
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | Name of the project             |
|                           |                         |                                 | 
|    Project                |                         |                                 |
|                           |                         |                                 |
|      .ProjectName         |                         |                                 | 
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | Integer                 |                                 |
|                           |                         |                                 | 
|    Project                |                         |                                 |
|                           |                         |                                 | 
|      .ServiceID           |                         |                                 | 
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | Decimal                 |                                 |
|                           |                         |                                 | 
|    Project                |                         |                                 |
|                           |                         |                                 | 
|      .Price               |                         |                                 | 
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | Currency paid for the           |
|                           |                         |                                 |
|    Project                |                         | project.  See glossary          |
|                           |                         |                                 | 
|      .Currency            |                         | for list of valid               |
|                           |                         |                                 |
|                           |                         | currencies.                     |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | String representing             |
|                           |                         |                                 |
|    Project                |                         | Date/Time (ISO 8601)            |
|                           |                         |                                 |
|      .CreationDate        |                         | that the Item was               |
|                           |                         |                                 |
|                           |                         | added to onDemand.              |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | String representing             |
|                           |                         |                                 |
|    Project                |                         | Date/Time (ISO 8601)            |
|                           |                         |                                 |
|     .DueDate              |                         | that the translation            |
|                           |                         |                                 |
|                           |                         | of the project is               |
|                           |                         |                                 |
|                           |                         | scheduled to be                 |
|                           |                         |                                 |
|                           |                         | completed.                      |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | String representing             |
|                           |                         |                                 |
|    Project                |                         | Date/Time (ISO 8601)            |
|                           |                         |                                 |
|      .CompletionDate      |                         | that the translation of         |
|                           |                         |                                 |
|                           |                         | the item was completed.         |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | See LanguageCode in             |
|                           |                         |                                 |
|    Project                |                         | glossary                        |
|                           |                         |                                 |
|      .SourceLanguage      |                         |                                 |
|                           |                         |                                 | 
|        .LanguageCode      |                         |                                 |
|                           |                         |                                 | 
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | Container               | Container containing            |
|                           |                         |                                 |
|    Project                |                         | target languages.               |
|                           |                         |                                 |
|      .TargetLanguages     |                         |                                 |
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+
| .. container:: notrans    | String                  | See LanguageCode in             |
|                           |                         |                                 |
|    Project                |                         | glossary                        |
|                           |                         |                                 |
|      .TargetLanguages     |                         |                                 |
|                           |                         |                                 |
|        .TargetLanguage    |                         |                                 |
|                           |                         |                                 |
|           .LanguageCode   |                         |                                 | 
|                           |                         |                                 |
+---------------------------+-------------------------+---------------------------------+


Response Body
=============


::

    <File>
      <AssetID>1711</AssetID>
      <Name>500errors.txt</Name>
      <Status>Rejected</Status>
      <SourceLanguage>
        <LanguageCode>
          <LanguageCode>en-gb</LanguageCode>
        </LanguageCode>
      </SourceLanguage>
      <TargetLanguage>
        <LanguageCode>es-us</LanguageCode>
      </TargetLanguage>
      <Rejection>
        <ReasonCode>5000</ReasonCode>
        <ReasonDescription>
            Failed .po file validation

            Failure Details:

            <![CDATA[
              #: od_api/exceptions.py:239 od_api/serializers.py:454
              msgid "Asset is already in use."
              msgstr "
                     ^^^^^ expected end quote
            ]>
        </ReasonDescription>
      </Rejection>
      <Project>
        <ProjectID>423</ProjectID>
        <URL>http://localhost:8000/api/projects/423</URL>
        <ProjectName>test job 1234</ProjectName>
        <Status>Complete</Status>
        <ServiceID>14</ServiceID>
        <Price>2947.86</Price>
        <Currency>EUR</Currency>
        <CreationDate>2015-10-21T16:56:51Z</CreationDate>
        <DueDate>2015-10-27T15:57:00Z</DueDate>
        <CompletionDate>2016-02-16T17:20:03Z</CompletionDate>
        <SourceLanguage>
          <LanguageCode>en-gb</LanguageCode>
        </SourceLanguage>
        <TargetLanguages>
          <TargetLanguage>
            <LanguageCode>he-il</LanguageCode>
          </TargetLanguage>
          <TargetLanguage>
            <LanguageCode>hi-in</LanguageCode>
          </TargetLanguage>
          <TargetLanguage>
            <LanguageCode>it-it</LanguageCode>
          </TargetLanguage>
          <TargetLanguage>
            <LanguageCode>pl-pl</LanguageCode>
          </TargetLanguage>
          <TargetLanguage>
            <LanguageCode>es-us</LanguageCode>
          </TargetLanguage>
        </TargetLanguages>
      </Project>
    </File>



Return Codes
============

+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Success                 | 202                     | Successful request      |
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
