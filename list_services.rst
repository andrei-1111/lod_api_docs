=============
List Services
=============

=============  ======================
**Resource:**  /api/services
**Method:**    GET
=============  ======================

This interface lists translation services that are available through the
API.

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

The response body includes a list of products.


+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| ServiceName             | String                  | Name of the sevice      |
+-------------------------+-------------------------+-------------------------+
| Description             | String                  | Description of the      |
|                         |                         |                         |
|                         |                         | service                 |
+-------------------------+-------------------------+-------------------------+
| PriceDescription        | String                  | Description of how      |
|                         |                         |                         |
|                         |                         | pricing works.          |
+-------------------------+-------------------------+-------------------------+
| ServiceID               | Integer                 | ID of the service       |
+-------------------------+-------------------------+-------------------------+
| SourceLanguages         | Container               | Source languages        |
|                         |                         |                         |
|                         |                         | available for this this |
|                         |                         |                         |
|                         |                         | service.                |
+-------------------------+-------------------------+-------------------------+
| SourceLanguages         | Container               | Container for Source    |
|                         |                         |                         |
| .SourceLanguage         |                         | Language                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| SourceLanguages         | String                  | See glossary for        |
|                         |                         |                         |
| .SourceLanguage         |                         | language code.          |
|                         |                         |                         |
| .LangaugeCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Target languages        |
|                         |                         |                         |
|                         |                         | available for this      |
|                         |                         |                         |
|                         |                         | service                 |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Container for Target    |
|                         |                         |                         |
| .TargetLanguage         |                         | Language                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | String                  | See glossary for        |
|                         |                         |                         |
| .TargetLanguage         |                         | language code.          |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| ValidInputs             | Container               | Contains source         |
|                         |                         |                         |
|                         |                         | content types that      |
|                         |                         |                         |
|                         |                         | this service can        |
|                         |                         |                         |  
|                         |                         | process                 |
+-------------------------+-------------------------+-------------------------+
| ValidInputs             | EmptyTag                | If this element exists  |
|                         |                         |                         |
| .Products               |                         | then this service       |
|                         |                         |                         |
|                         |                         | accepts Products        |
+-------------------------+-------------------------+-------------------------+
| ValidInputs             | Container               | Contains FileExtension  |
|                         |                         |                         |
| .Files                  |                         | elements for each       |
|                         |                         |                         |
|                         |                         | accepted file type.     |
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
| ValidInputs             | String                  | String representing     |
|                         |                         |                         |
| .Files                  |                         | an file extension       |
|                         |                         |                         |
| .FileExtension          |                         | that is accepted by the |
|                         |                         |                         |
|                         |                         | service.                |
+-------------------------+-------------------------+-------------------------+


Response Example
================

::

    <Services>
        <Service>
            <ServiceID>123</ServiceID>
            <Name>Service Name</Name>
            <Description>
                Service Description
            </Description>
            <PriceDescription>
                Around £1 per listing.
            </PriceDescription>
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
    </Services>