=============
Get Service
=============

+---------------+---------------------------------+
| **Resource:** | .. container:: notrans          |
|               |                                 |
|               |    /api/service/<<service id>>  |
+---------------+---------------------------------+
| **Method:**   | .. container:: notrans          |
|               |                                 |
|               |    GET                          |
+---------------+---------------------------------+

Provides detailed information about a single service


Arguments
=========

- **Service ID:** The ID of the Service. 


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

The response body details about a single service.
 

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | String                  | Name of the sevice      |
|                         |                         |                         |
|    Name                 |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Description of the      |
|                         |                         |                         |
|    Description          |                         | service                 |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Description of how      |
|                         |                         |                         |
|    PriceDescription     |                         | pricing works.          |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | ID of the service       |
|                         |                         |                         |
|    ServiceID            |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Source languages        |
|                         |                         |                         |
|    SourceLanguages      |                         | available for this this |
|                         |                         |                         |
|                         |                         | service.                |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container for Source    |
|                         |                         |                         |
|    SourceLanguages      |                         | Language                |
|                         |                         |                         |
|      .SourceLanguage    |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See glossary for        |
|                         |                         |                         |
|    SourceLanguages      |                         | language code.          |
|                         |                         |                         |
|      .SourceLanguage    |                         |                         |
|                         |                         |                         |
|      .LangaugeCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Target languages        |
|                         |                         |                         |
|    TargetLanguages      |                         | available for this      |
|                         |                         |                         |
|                         |                         | service                 |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container for Target    |
|                         |                         |                         |
|    TargetLanguages      |                         | Language                |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See glossary for        |
|                         |                         |                         |
|    TargetLanguages      |                         | language code.          |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Contains source         |
|                         |                         |                         |
|    ValidInputs          |                         | content types that      |
|                         |                         |                         |
|                         |                         | this service can        |
|                         |                         |                         |  
|                         |                         | process                 |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | EmptyTag                | If this element exists  |
|                         |                         |                         |
|    ValidInputs          |                         | then this service       |
|                         |                         |                         |
|      .Products          |                         | accepts Products        |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Contains FileExtension  |
|                         |                         |                         |
|    ValidInputs          |                         | elements for each       |
|                         |                         |                         |
|      .Files             |                         | accepted file type.     |
|                         |                         |                         |
|                         |                         | If files are not        |
|                         |                         |                         |
|                         |                         | supported by this       |
|                         |                         |                         |
|                         |                         | service, there will     |
|                         |                         |                         |
|                         |                         | be no Files element.    |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    ValidInputs          |                         | a file extension        |
|                         |                         |                         |
|      .Files             |                         | that is accepted by the |
|                         |                         |                         |
|      .FileExtension     |                         | service.                |
+-------------------------+-------------------------+-------------------------+
| MinimumUnits            | Integer                 | The minimum project size|
|                         |                         |                         |
|                         |                         | expressed in the number |
|                         |                         |                         |
|                         |                         | of units.               |
+-------------------------+-------------------------+-------------------------+
| UnitType                | String                  | The unit of measure for |
|                         |                         |                         |
|                         |                         | pricing the service.    |
|                         |                         |                         |
|                         |                         | Options are: words,     |
|                         |                         |                         |
|                         |                         | pages, standardized     |
|                         |                         |                         |
|                         |                         | pages, minutes, rows,   |
|                         |                         |                         |
|                         |                         | products, and files.    |
+-------------------------+-------------------------+-------------------------+



Response Example
================

::

    <Service>
        <ServiceID>123</ServiceID>
        <Name>Product Based Service</Name>
        <Description>
            Service Description
        </Description>
        <PriceDescription>
            Around £1 per listing.
        </PriceDescription>
        <ValidInputs>
            <Products/>
        </ValidInputs>
        <UnitType>products</UnitType>
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
