=============
Get Product
=============

+---------------+---------------------------------+
| **Resource:** | .. container:: notrans          |
|               |                                 |
|               |    /api/products/<<product id>> |
+---------------+---------------------------------+
| **Method:**   | .. container:: notrans          |
|               |                                 |
|               |    GET                          |
+---------------+---------------------------------+


Returns a product


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
|                         |                         | merchant owns.          |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body shows information about the product.


+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | Container               | Container of SKU        |
|                         |                         |                         |
|    SKUs                 |                         | elements                |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of a SKUs     |
|                         |                         |                         |
|    SKUs                 |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | SKU Number              |
|                         |                         |                         |
|    SKUs                 |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
|                         |                         |                         |
|      .SKUNumber         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | Internal onDemand ID    |
|                         |                         |                         |
|    AssetID              |                         | for the Asset.          |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String to download full |
|                         |                         |                         |
|    URL                  |                         | details of the product. |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | ID of the project that  |
|                         |                         |                         |
|    ProjectID            |                         | was used to translate   |
|                         |                         |                         |
|                         |                         | this item.  If SKU was  |
|                         |                         |                         |
|                         |                         | submitted multiple      |
|                         |                         |                         |
|                         |                         | times, it is the most   |
|                         |                         |                         |
|                         |                         | recent project.         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    SourceLanguagee      |                         | glossary                |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container containing    |
|                         |                         |                         |
|    TargetLanguages      |                         | target languages that   |
|                         |                         |                         |
|                         |                         | the product was already |
|                         |                         |                         |
|                         |                         | translated into.        |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    TargetLanguages      |                         | glossary                |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The status of the       |
|                         |                         |                         |
|    TargetLanguagess     |                         | translation             |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .Status            |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | URL to retrieve the     |
|                         |                         |                         |
|    TargetLanguages      |                         | project information.    |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .ProjectURL        |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | URL to download the     |
|                         |                         |                         |
|    Product              |                         | translated file.  See   |
|                         |                         |                         |
|      .TargetLanguages   |                         | GetTranslation          |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .DownloadURL       |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Contains the translated |
|                         |                         |                         |
|    Product              |                         | content                 |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .Translation       |                         |                         |
+-------------------------+-------------------------+-------------------------+
  

Response Example
================

::
 
    <Product>
        <SKUs>
            <SKU>
                <SKUNumber>123</SKUNumber>
            </SKU>
        </SKUs>
        <AssetID>9999</AssetID>
        <ProjectURL>https://</ProjectURL>
        <ProjectID>1234</ProjectID>
        <SourceLanguage>
            <LanguageCode>en-gb</LanguageCode>
        </SourceLanguage>
        <TargetLanguages>
            <TargetLanguage>
                <LanguageCode>de-de</LanguageCode>
                <Status>Complete</Complete>
                <ProjectURL>https://...</ProjectURL>
                <DownloadURL>https://...</DownloadURL>
                <Translation>
                    ...
                </Translation>
            </TargetLanguage>
            <TargetLanguage>
                <LanguageCode>fr-fr</LanguageCode>
                <Status>Complete</Complete>
                <ProjectURL>https://...</ProjectURL>
                <DownloadURL>https://..</DownloadURL>
                <Translation>
                    <Title>...</Title>
                    <Description>
                    <!-- Same structure as submitted -->
                    </Description>
                    <PrimaryCategory>123</PrimaryCategory>
                    <SKUs>
                        <SKU>
                            <SKUNumber>123</SKUNumber>
                            <ItemSpecifics>
                                <ItemSpecific>
                                    <SourceName>Colour</SourceName>
                                    <Name>Culeur</Name>
                                    <Value>Blanc</Value>
                                </ItemSpecific>
                                <ItemSpecific>
                                    <SourceName>Size</SourceName>
                                    <Name>Taille</Name>
                                    <Value>Grande</Value>
                                </ItemSpecific>
                            </ItemSpecifics>
                        </SKU>
                    </SKUs>
                </Translation>
            </TargetLanguage>
        </TargetLanguages>
    </Product>