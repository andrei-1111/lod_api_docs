=============
List Services
=============

+---------------+---------------------------------------+
| **Resource:** | /api/services                         |
+---------------+---------------------------------------+
| **Method:**   | GET                                   |
+---------------+---------------------------------------+


A key benefit of integrating with the Lionbridge onDemand API is that it gives you access to many different services.  At Lionbridge, we define a service as a set of processes that we can execute for you.  We have services for different quality levels (ranging from raw machine translation to professional translation by domain specialists).  We also have content-specific services. For example, we can `subtitle your videos <https://ondemand.lionbridge.com/service-detail/1/video-translation-multilingual-video-subtitling>`_.

This interface lists translation services that are available through the
API.

**New in version 2014-09-04**

The list services api now includes a minimum units element.  If the minimum units is 500 words,
a 400 word project would be priced the same as a 500 word project.  The unit minimum is applied
at the project level.

**New in version 2014-06-10**

To better support file-based services, version 2014-06-10 now has a valid inputs
element.  If the service is a file-based service, this element will list the 
file types that are supported by this service.

Services can be filtered by their support of different input formats by using the URL /api/services?extension=<<extension>>.  See the extension argument below.



Arguments
=========

The List Services API can filter services using query string arguments.  The supported filtering arguments are listed below.

- **extension:** This is a file extension such as "docx". For example, the URL /api/services?extension=docx will return all services that accept Microsoft Word documents as an input format.  If you are looking for services that accept products, use /api/services?extension=product .  If you would like a list of services that support both docx _and_ doc, you can use ?extension=doc+docx.  If you would like a service that supports _either_ docx _or_ doc, use ?extension=doc,docx.  

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
| Name                    | String                  | Name of the sevice      |
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
| .Files                  |                         | a file extension        |
|                         |                         |                         |
| .FileExtension          |                         | that is accepted by the |
|                         |                         |                         |
|                         |                         | service.                |
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

    <Services>
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
         <Service>
            <ServiceID>123</ServiceID>
            <Name>File Based Service</Name>
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
            <MinimumUnits>500</MinimumUnits>

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