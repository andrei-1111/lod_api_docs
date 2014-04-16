=============
Get Project
=============

=============  ============================
**Resource:**  /api/projects/<<project id>>
**Method:**    GET
=============  ============================

Retrieves information about a project.  If the project is complete, the
request will return all of the translated products associated with the
project.


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

The response body shows information about the project.

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| ProjectID               | Integer                 | onDemand ID of the      |
|                         |                         |                         | 
|                         |                         | project                 |
+-------------------------+-------------------------+-------------------------+
| Status                  | String                  | Status of the project   |
+-------------------------+-------------------------+-------------------------+
| ServiceID               | Integer                 |                         |
+-------------------------+-------------------------+-------------------------+
| TotalPrice              | Decimal                 |                         |
+-------------------------+-------------------------+-------------------------+
| Currency                | String                  | Currency paid for the   |
|                         |                         |                         |
|                         |                         | project.  See glossary  |
|                         |                         |                         |
|                         |                         | for list of valid       |
|                         |                         |                         |
|                         |                         | currencies.             |
+-------------------------+-------------------------+-------------------------+
| CreationDate            | String                  | String representing     |
|                         |                         |                         |
|                         |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the Item was      |
|                         |                         |                         |
|                         |                         | added to onDemand.      |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| DueDate                 | String                  | String representing     |
|                         |                         |                         |
|                         |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the translation   |
|                         |                         |                         |
|                         |                         | of the item is          |
|                         |                         |                         |
|                         |                         | scheduled to be         |
|                         |                         |                         |
|                         |                         | completed.              |
+-------------------------+-------------------------+-------------------------+
| CompletionDate          | String                  | String representing     |
|                         |                         |                         |
|                         |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         | that the translation of |
|                         |                         |                         |
|                         |                         | the item was completed. |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| SourceLanguage.Language | String                  | See LanguageCode in     |
|                         |                         |                         |
| Code                    |                         | glossary                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Container containing    |
|                         |                         |                         |
|                         |                         | target languages.       |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | String                  | See LanguageCode in     |
|                         |                         |                         |
| .TargetLanguages        |                         | glossary                |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Container of Items      |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Container of Item       |
|                         |                         |                         |
| .Product                |                         | information             |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | The SKU of the item     |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Integer                 | The internal Asset ID   |
|                         |                         |                         |
| .Product                |                         | of the product.         |
|                         |                         |                         |
| .AssetID                |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Container containing    |
|                         |                         |                         |
| .Product                |                         | target languages.       |
|                         |                         |                         |
| .TargetLanguages        |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | See LanguageCode in     |
|                         |                         |                         |
| .Product                |                         | glossary                |
|                         |                         |                         |
| .TargetLanguages        |                         |                         |
|                         |                         |                         |
| .TargetLanguage         |                         |                         |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | URL to retrieve this    |
|                         |                         |                         |
| .Product                |                         | particular translation. |
|                         |                         |                         |
| .TargetLanguages        |                         |                         |
|                         |                         |                         |
| .TargetLanguage         |                         |                         |
|                         |                         |                         |
| .URL                    |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Container Element for   |
|                         |                         |                         |
| .Product                |                         | translated content. The |
|                         |                         |                         |
| .TargetLanguages        |                         | description will use    |
|                         |                         |                         |
| .TargetLanguage         |                         | the same structure as   |
|                         |                         |                         |
| .Translation            |                         | the source content.     |
|                         |                         |                         |
|                         |                         |  Only ItemSpecifics     |
|                         |                         |                         |
|                         |                         | that are recommended or |
|                         |                         |                         |
|                         |                         | required on the target  |
|                         |                         |                         |
|                         |                         | language will be        |
|                         |                         |                         |
|                         |                         | returned.  The API will |
|                         |                         |                         |
|                         |                         | add an additional node  |
|                         |                         |                         |
|                         |                         | called “SourceName” on  |
|                         |                         |                         |
|                         |                         | each ItemSpecific       |
+-------------------------+-------------------------+-------------------------+

  

Response Example
================

::

    <Project>
        <ProjectID>10001</ProjectID>
        <Status>Complete</ProjectStatus>
        <ServiceID>14</ServiceID>
        <TotalWords>1000</TotalWords>
        <Price>1000.00</Price>
        <Currency>EUR</Currency>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <DueDate>2014-01-25T10:32:02Z</DueDate>
        <CompletionDate>2014-01-25T10:32:02Z</CompletionDate>
        <SourceLanguage>
            <LanguageCode>en-uk</LanguageCode>
        </SourceLanguage>
        <TargetLanguages>
            <TargetLanguage>
                <LanguageCode>de-de</LanguageCode>
            </TargetLanguage>
            <TargetLanguage>
                <LanguageCode>fr-fr</LanguageCode>
            </TargetLanguage>
        </TargetLanguages>
        <Products>
            <Product>
                <AssetID>9999</AssetID>
                <SKUs>
                    <SKU>
                        <SKUNumber>123</SKUNumber>
                    </SKU>
                </SKUs>
                <TargetLanguages>
                    <TargetLanguage>
                        <LanguageCode>it-it</LanguageCode>
                        <URL>https://</URL>
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
                    ...
                </TargetLanguages>
            </Product>
        </Products>
    </Project>