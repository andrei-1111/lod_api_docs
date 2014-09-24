=============
List Services
=============

+---------------+------------------------+
| **Resource:** | .. container:: notrans |
|               |                        |
|               |    /api/services       |
+---------------+------------------------+
| **Method:**   | .. container:: notrans |
|               |                        |
|               |    GET                 |
+---------------+------------------------+


A key benefit of integrating with the Lionbridge onDemand API is that it gives you access to many different services.  At Lionbridge, we define a service as a set of processes that we can execute for you.  We have services for different quality levels (ranging from raw machine translation to professional translation by domain specialists).  We also have content-specific services. For example, we can `subtitle your videos <https://ondemand.lionbridge.com/service-detail/1/video-translation-multilingual-video-subtitling>`_.

This interface lists translation services that are available through the
API.

**New in version 2014-06-10**

To better support file-based services, version 2014-06-10 now has a valid inputs
element.  If the service is a file-based service, this element will list the 
file types that are supported by this service.

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