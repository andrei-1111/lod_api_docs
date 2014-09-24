=============
List Products
=============

+---------------+------------------------+
| **Resource:** | .. container:: notrans |
|               |                        |
|               |    /api/products       |
+---------------+------------------------+
| **Method:**   | .. container:: notrans |
|               |                        |
|               |    GET                 |
+---------------+------------------------+


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
| .. container:: notrans  | Container               | Container of Product           |
|                         |                         |                                |
|    Product              |                         | information                    |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | Container               | Container of SKU               |
|                         |                         |                                |
|    Product              |                         | elements                       |
|                         |                         |                                |
|      .SKUs              |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | Container               | Container of SKU Number        |
|                         |                         |                                |
|    Product              |                         |                                |
|                         |                         |                                |
|      .SKUs              |                         |                                |
|                         |                         |                                |
|      .SKU               |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | SKU Number                     |
|                         |                         |                                |
|    Product              |                         |                                |
|                         |                         |                                |
|      .SKUs              |                         |                                |
|                         |                         |                                |
|      .SKU               |                         |                                |
|                         |                         |                                |
|      .SKUNumber         |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | Integer                 | Internal onDemand ID           |
|                         |                         |                                |
|    Product              |                         | for the Asset.                 |
|                         |                         |                                |
|      .AssetID           |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | String to download full        |
|                         |                         |                                |
|    Product              |                         | details of the product.        |
|                         |                         |                                |
|      .URL               |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | Integer                 | ID of the project that         |
|                         |                         |                                |
|    Product              |                         | was used to translate          |
|                         |                         |                                |
|      .ProjectID         |                         | this item.  If SKU was         |
|                         |                         |                                |
|                         |                         | submitted multiple             |
|                         |                         |                                |
|                         |                         | times, it is the most          |
|                         |                         |                                |
|                         |                         | recent project.                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | See LanguageCode in            |
|                         |                         |                                |
|    Product              |                         | glossary                       |
|                         |                         |                                |
|      .SourceLanguage    |                         |                                |
|                         |                         |                                |
|      .LanguageCode      |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | Container               | Container containing           |
|                         |                         |                                |
|    Product              |                         | target languages that          |
|                         |                         |                                |
|      .TargetLanguages   |                         | the product was already        |
|                         |                         |                                |
|                         |                         | translated into.               |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | See LanguageCode in            |
|                         |                         |                                |
|    Product              |                         | glossary                       |
|                         |                         |                                |
|      .TargetLanguages   |                         |                                |
|                         |                         |                                |
|      .TargetLanguage    |                         |                                |
|                         |                         |                                |
|      .LanguageCode      |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | The status of the              |
|                         |                         |                                |
|    Product              |                         | translation                    |
|                         |                         |                                |
|      .TargetLanguages   |                         |                                |
|                         |                         |                                |
|      .TargetLanguage    |                         |                                |
|                         |                         |                                |
|      .Status            |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | URL to retrieve the            |
|                         |                         |                                |
|    Product              |                         | project information.           |
|                         |                         |                                |
|      .TargetLanguages   |                         |                                |
|                         |                         |                                |
|      .TargetLanguage    |                         |                                |
|                         |                         |                                |
|      .ProjectURL        |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | URL to download the            |
|                         |                         |                                |
|    Product              |                         | translated file.  See          |
|                         |                         |                                |
|      .TargetLanguages   |                         | :doc:`get_product_translation` |
|                         |                         |                                |
|      .TargetLanguage    |                         |                                |
|                         |                         |                                |
|      .DownloadURL       |                         |                                |
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