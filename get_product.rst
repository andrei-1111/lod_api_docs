=============
Get Product
=============

=============  ======================
**Resource:**  /api/products/<<product id>
**Method:**    GET
=============  ======================

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
| SKUs                    | Container               | Container of SKU        |
|                         |                         |                         |
|                         |                         | elements                |
+-------------------------+-------------------------+-------------------------+
| SKUs                    | Container               | Container of a SKUs     |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| SKUs                    | String                  | SKU Number              |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .SKUNumber              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| AssetID                 | Integer                 | Internal onDemand ID    |
|                         |                         |                         |
|                         |                         | for the Asset.          |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| URL                     | String                  | String to download full |
|                         |                         |                         |
|                         |                         | details of the product. |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| ProjectID               | Integer                 | ID of the project that  |
|                         |                         |                         |
|                         |                         | was used to translate   |
|                         |                         |                         |
|                         |                         | this item.  If SKU was  |
|                         |                         |                         |
|                         |                         | submitted multiple      |
|                         |                         |                         |
|                         |                         | times, it is the most   |
|                         |                         |                         |
|                         |                         | recent project.         |
+-------------------------+-------------------------+-------------------------+
| SourceLanguagee         | String                  | See LanguageCode in     |
|                         |                         |                         |
| .LanguageCode           |                         | glossary                |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Container containing    |
|                         |                         |                         |
|                         |                         | target languages that   |
|                         |                         |                         |
|                         |                         | the product was already |
|                         |                         |                         |
|                         |                         | translated into.        |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | String                  | See LanguageCode in     |
|                         |                         |                         |
| .TargetLanguage         |                         | glossary                |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguagess        | String                  | The status of the       |
|                         |                         |                         |
| .TargetLanguage         |                         | translation             |
|                         |                         |                         |
| .Status                 |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | String                  | URL to retrieve the     |
|                         |                         |                         |
| .TargetLanguage         |                         | project information.    |
|                         |                         |                         |
| .ProjectURL             |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Product                 | String                  | URL to download the     |
|                         |                         |                         |
| .TargetLanguages        |                         | translated file.  See   |
|                         |                         |                         |
| .TargetLanguage         |                         | GetTranslation          |
|                         |                         |                         |
| .DownloadURL            |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Product                 | Container               | Contains the translated |
|                         |                         |                         |
| .TargetLanguages        |                         | content                 |
|                         |                         |                         |
| .TargetLanguage         |                         |                         |
|                         |                         |                         |
| .Translation            |                         |                         |
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