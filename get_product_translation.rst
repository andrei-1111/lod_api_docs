=======================
Get Product Translation
=======================

=============  ============================================
**Resource:**  /api/products/<<asset id>>/<<Language Code>>
**Method:**    GET
=============  ============================================

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
| SKUs                    | Container               | Container of a SKU      |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| SKUS                    | String                  | SKU Number              |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .SKUNumber              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| AssetID                 | Integer                 | The internal onDemand   |
|                         |                         |                         |
|                         |                         | ID for the product.     |
+-------------------------+-------------------------+-------------------------+
| SourceTitle             | String                  | The title of the source |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         | listing                 |
+-------------------------+-------------------------+-------------------------+
| Service                 | Integer                 | The service used to     |
|                         |                         |                         |
|                         |                         | translate the item.     |
+-------------------------+-------------------------+-------------------------+
| Language                | String                  | Language Code of        |
|                         |                         |                         |
|                         |                         | language translated     |
|                         |                         | into.                   |
+-------------------------+-------------------------+-------------------------+
| TranslatedFields        | Container               | Contains translations   |
|                         |                         |                         |
|                         |                         | of all of the           |
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
    