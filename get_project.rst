=============
Get Project
=============

+---------------+---------------------------------+
| **Resource:** | .. container:: notrans          |
|               |                                 |
|               |    /api/projects/<<project id>> |
+---------------+---------------------------------+
| **Method:**   | .. container:: notrans          |
|               |                                 |
|               |    GET                          |
+---------------+---------------------------------+

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
| Not Found               | 404                     | The URL does not relate |
|                         |                         |                         |
|                         |                         | to a project that the   |
|                         |                         |                         |
|                         |                         | account owns.           |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body shows information about the project.

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | Integer                 | onDemand ID of the      |
|                         |                         |                         | 
|    ProjectID            |                         | project                 |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Status of the project   |
|                         |                         |                         | 
|    Status               |                         |                         | 
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 |                         |
|                         |                         |                         | 
|    ServiceID            |                         |                         | 
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 |                         |
|                         |                         |                         | 
|    TotalPrice           |                         |                         | 
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Currency paid for the   |
|                         |                         |                         |
|    Currency             |                         | project.  See glossary  |
|                         |                         |                         |
|                         |                         | for list of valid       |
|                         |                         |                         |
|                         |                         | currencies.             |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    CreationDate         |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the Item was      |
|                         |                         |                         |
|                         |                         | added to onDemand.      |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    DueDate              |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         |  that the translation   |
|                         |                         |                         |
|                         |                         | of the item is          |
|                         |                         |                         |
|                         |                         | scheduled to be         |
|                         |                         |                         |
|                         |                         | completed.              |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    CompletionDate       |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         | that the translation of |
|                         |                         |                         |
|                         |                         | the item was completed. |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    SourceLanguage       |                         | glossary                |
|                         |                         |                         | 
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container containing    |
|                         |                         |                         |
|    TargetLanguages      |                         | target languages.       |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    TargetLanguages      |                         | glossary                |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         | 
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of Products.  |
|                         |                         |                         |
|    Products             |                         | This element will be    |
|                         |                         |                         |
|                         |                         | empty if this project   |
|                         |                         |                         |
|                         |                         | contiains fils instead  |
|                         |                         |                         |
|                         |                         | of products.            |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of Item       |
|                         |                         |                         |
|    Products             |                         | information             |
|                         |                         |                         |
|      .Product           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The SKU of the item     |
|                         |                         |                         |
|    Products             |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | The internal Asset ID   |
|                         |                         |                         |
|    Products             |                         | of the product.         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .AssetID           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container containing    |
|                         |                         |                         |
|    Products             |                         | target languages.       |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    Products             |                         | glossary                |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | URL to retrieve this    |
|                         |                         |                         |
|    Products             |                         | particular translation. |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .URL               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container Element for   |
|                         |                         |                         |
|    Products             |                         | translated content. The |
|                         |                         |                         |
|      .Product           |                         | description will use    |
|                         |                         |                         |
|      .TargetLanguages   |                         | the same structure as   |
|                         |                         |                         |
|      .TargetLanguage    |                         | the source content.     |
|                         |                         |                         |
|      .Translation       |                         |  Only ItemSpecifics     |
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
| .. container:: notrans  | Container               | Contains file elements. |
|                         |                         |                         |
|    Files                |                         | It will be empty on     |
|                         |                         |                         |
|                         |                         | projects that have      |
|                         |                         |                         |
|                         |                         | products instead of     |
|                         |                         |                         |
|                         |                         | files.                  |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | Asset ID of the file.   |
|                         |                         |                         |
|    Files                |                         |                         |
|                         |                         |                         |
|      .File              |                         |                         |
|                         |                         |                         |
|      .AssetID           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Original name of the    |
|                         |                         |                         |
|    Files                |                         | file.                   |
|                         |                         |                         |
|      .File              |                         |                         |
|                         |                         |                         |
|      .FileName          |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | URL to download the     |
|                         |                         |                         |
|    Files                |                         | source file.            |
|                         |                         |                         |
|      .File              |                         |                         |
|                         |                         |                         |
|      .URL               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container containing    |
|                         |                         |                         |
|    Files                |                         | target languages.       |
|                         |                         |                         |
|      .File              |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See LanguageCode in     |
|                         |                         |                         |
|    Files                |                         | glossary                |
|                         |                         |                         |
|      .File              |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    Files                |                         | the url to download     |
|                         |                         |                         |
|      .File              |                         | the translated file.    |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .URL               |                         |                         |
+-------------------------+-------------------------+-------------------------+





Response Examples
=================

Example of get project response for product-based projects.

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
            <LanguageCode>en-gb</LanguageCode>
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

Example of get project response for file-based projects.

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
            <LanguageCode>en-gb</LanguageCode>
        </SourceLanguage>
        <TargetLanguages>
            <TargetLanguage>
                <LanguageCode>de-de</LanguageCode>
            </TargetLanguage>
            <TargetLanguage>
                <LanguageCode>fr-fr</LanguageCode>
            </TargetLanguage>
        </TargetLanguages>
        <Files>
            <File>
                <AssetID>1111</AssetID>
                <FileName>foo.txt</FileName>
                <URL>https...</URL>
                <TargetLanguages>
                    <TargetLanguage>
                        <LanguageCode>it-it</LanguageCode>
                        <URL>https://</URL>
                    </TargetLanguage>
                    ...
                </TargetLanguages>
            </File>   
        </Files>
    </Project>