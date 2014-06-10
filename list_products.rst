=============
List Products
=============

=============  ======================
**Resource:**  /api/products
**Method:**    GET
=============  ======================

Returns a list of all products submitted by the merchant

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


+-------------------------+-------------------------+--------------------------------+
| Property                | Type                    | Comments                       |
+=========================+=========================+================================+
| Product                 | Container               | Container of Product           |
|                         |                         |                                |
|                         |                         | information                    |
+-------------------------+-------------------------+--------------------------------+
| Product                 | Container               | Container of SKU               |
|                         |                         |                                |
| .SKUs                   |                         | elements                       |
+-------------------------+-------------------------+--------------------------------+
| Product                 | Container               | Container of SKU Number        |
|                         |                         |                                |
| .SKUs                   |                         |                                |
|                         |                         |                                |
| .SKU                    |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | SKU Number                     |
|                         |                         |                                |
| .SKUs                   |                         |                                |
|                         |                         |                                |
| .SKU                    |                         |                                |
|                         |                         |                                |
| .SKUNumber              |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | Integer                 | Internal onDemand ID           |
|                         |                         |                                |
| .AssetID                |                         | for the Asset.                 |
|                         |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | String to download full        |
|                         |                         |                                |
| .URL                    |                         | details of the product.        |
|                         |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | Integer                 | ID of the project that         |
|                         |                         |                                |
| .ProjectID              |                         | was used to translate          |
|                         |                         |                                |
|                         |                         | this item.  If SKU was         |
|                         |                         |                                |
|                         |                         | submitted multiple             |
|                         |                         |                                |
|                         |                         | times, it is the most          |
|                         |                         |                                |
|                         |                         | recent project.                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | See LanguageCode in            |
|                         |                         |                                |
| .SourceLanguage         |                         | glossary                       |
|                         |                         |                                |
| .LanguageCode           |                         |                                |
|                         |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | Container               | Container containing           |
|                         |                         |                                |
| .TargetLanguages        |                         | target languages that          |
|                         |                         |                                |
|                         |                         | the product was already        |
|                         |                         |                                |
|                         |                         | translated into.               |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | See LanguageCode in            |
|                         |                         |                                |
| .TargetLanguages        |                         | glossary                       |
|                         |                         |                                |
| .TargetLanguage         |                         |                                |
|                         |                         |                                |
| .LanguageCode           |                         |                                |
|                         |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | The status of the              |
|                         |                         |                                |
| .TargetLanguages        |                         | translation                    |
|                         |                         |                                |
| .TargetLanguage         |                         |                                |
|                         |                         |                                |
| .Status                 |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | URL to retrieve the            |
|                         |                         |                                |
| .TargetLanguages        |                         | project information.           |
|                         |                         |                                |
| .TargetLanguage         |                         |                                |
|                         |                         |                                |
| .ProjectURL             |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| Product                 | String                  | URL to download the            |
|                         |                         |                                |
| .TargetLanguages        |                         | translated file.  See          |
|                         |                         |                                |
| .TargetLanguage         |                         | :doc:`get_product_translation` |
|                         |                         |                                |
| .DownloadURL            |                         |                                |
+-------------------------+-------------------------+--------------------------------+

  

Response Example
================

::

    <Products>
        <Product>
            <SKUs>
                <SKU>
                    <SKUNumber>123</SKUNumber>
                </SKU>
            </SKUs>
            <AssetID>9999</AssetID>
            <ProjectID>1234</ProjectID>
            <SourceLanguage>
                <LanguageCode>en-gb</LanguageCode>
            </SourceLanguage>
            <TargetLanguages>
                <TargetLanguage>
                    <LanguageCode>de-de</LanguageCode>
                    <Status>Complete</Status>
                    <ProjectURL>https://</ProjectURL>
                    <DownloadURL>https://ondemand…</DownloadURL>
                </TargetLanguage>
                <TargetLanguage>
                    <LanguageCode>fr-fr</LanguageCode>
                    <Status>Complete</Status>
                    <ProjectURL>https://</ProjectURL>
                    <DownloadURL>https://liondemand.com<DownloadURL>
                </TargetLanguage>
            </TargetLanguages>
        </Product>
    <Products>