=======================
Get Product Translation
=======================

+---------------+-------------------------------------------------+
| **Resource:** | .. container:: notrans                          |
|               |                                                 |
|               |    /api/products/<<asset id>>/<<Language Code>> |
+---------------+-------------------------------------------------+
| **Method:**   | .. container:: notrans                          |
|               |                                                 |
|               |    GET                                          |
+---------------+-------------------------------------------------+


Retrieves the translation of an item


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
|                         |                         | account owns. Or a      |
|                         |                         |                         |
|                         |                         | translation in this     |
|                         |                         |                         |
|                         |                         | language does not exist |
|                         |                         |                         |
|                         |                         | for this product.       |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body shows information about the product.


+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | Container               | Container of SKU        |
|                         |                         |                         |
|    SKUs                 |                         | elements.               |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of a SKU.     |
|                         |                         |                         |
|    SKUs                 |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | SKU Number              |
|                         |                         |                         |
|    SKUS                 |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
|                         |                         |                         |
|      .SKUNumber         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | The internal onDemand   |
|                         |                         |                         |
|    AssetID              |                         | ID for the product.     |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The title of the source |
|                         |                         |                         |
|    SourceTitle          |                         | listing.                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | The service used to     |
|                         |                         |                         |
|    Service              |                         | translate the item.     |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Language Code of        |
|                         |                         |                         |
|    Language             |                         | language translated     |
|                         |                         | into.                   |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Contains translations   |
|                         |                         |                         |
|    TranslatedFields     |                         | of all of the           |
|                         |                         |                         |
|                         |                         | translated fields.      |
+-------------------------+-------------------------+-------------------------+


  

Response Example
================

::
 
    <Translation>
        <SKUs>
            <SKU>
                <SKUNumber>123</SKUNumber>
            </SKU>
        </SKUs>
        <AssetID>9999</AssetID>
        <SourceTitle>Men&apos;s Pants</SourceTitle>
        <Service>14</Service>
        <Language>de-de</Language>
        <TranslatedFields>
            <Title>...</Title>
            <Description>
                <!-- Same structure as submitted -->
            </Description>
            <PrimaryCategory>123</PrimaryCategory>
            <SKUS>
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
            <SKUs>
        </TranslatedFields>
    </Translation>
    