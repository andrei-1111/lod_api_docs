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

The response body shows information about the product.


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
| .. container:: notrans  | Container               | If the file is          |
|                         |                         |                         |
|    Project              |                         | associated with a       |
|                         |                         |                         |
|                         |                         | project, this element   |
|                         |                         |                         |
|                         |                         | will contain            |
|                         |                         |                         |
|                         |                         | information about       |
|                         |                         |                         |
|                         |                         | the project.            |
+-------------------------+-------------------------+-------------------------+
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
| .. container:: notrans  | Container               | If the file is not      |
|                         |                         |                         |
|    AvailableServices    |                         | associated with a       |
|                         |                         |                         |
|                         |                         | project, the API will   |
|                         |                         |                         |
|                         |                         | list services that it   |
|                         |                         |                         |
|                         |                         | could be used with.     |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | ID of the service       |
|                         |                         |                         |
|    AvailableServices    |                         |                         |
|                         |                         |                         |
|      .Service           |                         |                         |
|                         |                         |                         |
|      .ServiceID         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Name of the sevice      |
|                         |                         |                         |
|    AvailableServices    |                         |                         |
|                         |                         |                         |
|      .Service           |                         |                         |
|                         |                         |                         |
|      .Name              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Description of the      |
|                         |                         |                         |
|    AvailableServices    |                         | service                 |
|                         |                         |                         |
|      .Service           |                         |                         |
|                         |                         |                         |
|      .Description       |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Description of how      |
|                         |                         |                         |
|    AvailableServices    |                         | pricing works           |
|                         |                         |                         |
|      .Service           |                         |                         |
|                         |                         |                         |
|      .PriceDescription  |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Source languages        |
|                         |                         |                         |
|    AvailableServices    |                         | available for this      |
|                         |                         |                         |
|      .Service           |                         | service.                |
|                         |                         |                         |
|      .SourceLanguages   |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See glossary for        |
|                         |                         |                         |
|    AvailableServices    |                         | language code.          |
|                         |                         |                         |
|      .Service           |                         |                         |
|                         |                         |                         |
|      .SourceLanguages   |                         |                         |
|                         |                         |                         |
|      .LangaugeCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Target languages        |
|                         |                         |                         |
|    AvailableServices    |                         | available for this      |
|                         |                         |                         |
|      .Service           |                         | service.                |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See glossary for        |
|                         |                         |                         |
|    AvailableServices    |                         | language code.          |
|                         |                         |                         |
|      .Service           |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Contains content types  |
|                         |                         |                         |
|    AvailableServices    |                         | that this service       |
|                         |                         |                         |
|      .Service           |                         | accepts.                |
|                         |                         |                         |
|      .ValidInputs       |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         |                         |  
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Contains FileExtension  |
|                         |                         |                         |
|    AvailableServices    |                         | that this service       |
|                         |                         |                         |
|      .Service           |                         | accepts.                |
|                         |                         |                         |
|      .ValidInputs       |                         |                         |
|                         |                         |                         |
|      .Files             |                         |                         |
|                         |                         |                         |
|      .FileExtension     |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The unit of measure for |
|                         |                         |                         |
|    AvailableServices    |                         | pricing the service     |
|                         |                         |                         |
|      .Service           |                         | Options are words, pages|
|                         |                         |                         |
|      .UnitType          |                         | standardized pages,     |
|                         |                         |                         |
|                         |                         | minutes, rows, and files|
|                         |                         |                         |
|                         |                         | products, and files.    |
+-------------------------+-------------------------+-------------------------+  
| .. container:: notrans  | Integer                 | The minimum project size|
|                         |                         |                         |
|    AvailableServices    |                         | expressed in the number |
|                         |                         |                         |
|      .Service           |                         | of units.  See UnitType |
|                         |                         |                         |
|      .MinimumUnits      |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+

Response Example
================

::
 
    <File>
        <AssetID>123456</AssetID>
        <Name>Foo.txt</Name>
        <Status>Analyzed</Status>
        <SourceLanguage>
            <LanguageCode>en-gb</LanguageCode>
        </SourceLanguage>
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
        <AvailableServices>
            <Service>
                <ServiceID>123</ServiceID>
                <Name>Machine Translation</Name>
                <Description>
                    Service Description
                </Description>
                <PriceDescription>
                    Around £1 per listing.
                </PriceDescription>
                <ValidInputs>
                    <Files>
                        <FileExtension>xls</FileExtension>
                        <FileExtension>docx</FileExtension>
                    </Files>
                </ValidInputs>
                <UnitType>words</UnitType>
                <MinimumUnits>10</MinimumUnits>
                <SourceLanguages>
                    <SourceLanguage>
                        <LanguageCode>de-de</LanguageCode>
                    </SourceLanguage>
                    <SourceLanguage>
                        <LanguageCode>en-us</LanguageCode>
                    </SourceLanguage>
                </SourceLanguages>
                <TargetLanguages>
                    <TargetLanguage>
                        <LanguageCode>de-de</LanguageCode>
                    </TargetLanguage>
                    <TargetLanguage>
                        <LanguageCode>fr-fr</LanguageCode>
                    </TargetLanguage>
                </TargetLanguages>
            </Service>
    
        </AvailableServices>
    </File>
