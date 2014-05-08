==============
Generate Quote
==============

=============  ===================
**Resource:**  /api/quote/generate
**Method:**    POST
=============  ===================

This interface is used to generate a quote.  A quote can contain multiple projects.

Request Body
============

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | Container               | Contains information    |
|                         |                         |                         |
|                         |                         | specifying the          |
|                         |                         |                         |
|                         |                         | translation project.    |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | String                  | String representing     |
|                         |                         |                         |
|  .Currency              |                         | currency that the       |
|                         |                         |                         |
|                         |                         | merchant wishes to pay  |
|                         |                         |                         |
|                         |                         | with. See glossary for  |
|                         |                         |                         |
|                         |                         | list of valid           |
|                         |                         |                         |
|                         |                         | currencies.             |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | String                  | When the item has been  |
|                         |                         |                         |
| .NotificationURL        |                         | translated, the API     |
|                         |                         |                         |
|                         |                         | will send a POST        |
|                         |                         |                         |
|                         |                         | request to this URL.    |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | Integer                 | Numeric service code    |
|                         |                         |                         |
| .ServiceID              |                         | for the translation     |
|                         |                         |                         |
|                         |                         | service.  The service   |
|                         |                         |                         |
|                         |                         | defines a set of        |
|                         |                         |                         |
|                         |                         | options such as machine |
|                         |                         |                         |
|                         |                         | translation with post   |
|                         |                         |                         |
|                         |                         | edit on the title and   |
|                         |                         |                         |
|                         |                         | raw machine translation |
|                         |                         |                         |
|                         |                         | on the body.  This      |
|                         |                         |                         |
|                         |                         | element is optional.    |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | Container               | Contains 1 source       |
|                         |                         |                         |
| .SourceLanguage         |                         | language                |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | String                  | See LanguageCode in     |
|                         |                         |                         |
| .SourceLanguage         |                         | glossary                |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | Container               | Contains 1 or more      |
|                         |                         |                         |
| .TargetLanguages        |                         | target languages        |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | String                  | See LanguageCode in     |
|                         |                         |                         |
| .TargetLanguages        |                         | glossary                |
|                         |                         |                         |
| .TargetLanguage         |                         |                         |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | List                    | List of Product         |
|                         |                         | Elements                |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | The title of the        |
|                         |                         |                         |
| .Product                |                         | product                 |
|                         |                         |                         |
| .Title                  |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Integer                 | ID of the product’s     |
|                         |                         |                         |
| .Product                |                         | primary category        |
|                         |                         |                         |
| .PrimaryCategory        |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Integer                 | ID of the top level     |
|                         |                         |                         |
| .Product                |                         | category that the       |
|                         |                         |                         |
| .TopLevelCategory       |                         | product sits in         |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | Delimited string        |
|                         |                         |                         |
| .Product                |                         | showing the path        |
|                         |                         |                         |
| .Category               |                         | through the category    |
|                         |                         |                         |
|                         |                         | hierarchy to the        |
|                         |                         |                         |
|                         |                         | primary category.  This |
|                         |                         |                         |
|                         |                         | is mainly for           |
|                         |                         |                         |
|                         |                         | contextual information  |
|                         |                         |                         |
|                         |                         | for the translators.    |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | The description of the  |
|                         |                         |                         |
| .Product                |                         | item.  This element can |
|                         |                         |                         |
| .Description            |                         | contain sub-elements.   |
|                         |                         |                         |
|                         |                         | HTML that is not well   |
|                         |                         |                         |
|                         |                         | formed XML should be    |
|                         |                         |                         |
|                         |                         | wrapped in CDATA tags.  |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Contains a SKU elements |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Contains a SKU Number   |
|                         |                         |                         |
| .Product                |                         | and a list of           |
|                         |                         |                         |
| .SKUs                   |                         | ItemSpecifics that are  |
|                         |                         |                         |
| .SKU                    |                         | relevant to the SKU     |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | SKU Number              |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .SKUNumber              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Contains elements       |
|                         |                         |                         |
| .Product                |                         | representing            |
|                         |                         |                         |
| .SKUs                   |                         | specifications.         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .ItemSpecifics          |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Contains elements       |
|                         |                         |                         |
| .Product                |                         | representing name-value |
|                         |                         |                         |
| .SKUs                   |                         | pairs                   |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .ItemSpecifics          |                         |                         |
|                         |                         |                         |
| .NameValueList          |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Contains a single       |
|                         |                         |                         |
| .Product                |                         | name-value pair         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .ItemSpecifics          |                         |                         |
|                         |                         |                         |
| .NameValueList          |                         |                         |
|                         |                         |                         |
| .NameValue              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | The name of the name    |
|                         |                         |                         |
| .Product                |                         | value pair              |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .ItemSpecifics          |                         |                         |
|                         |                         |                         |
| .NameValueList          |                         |                         |
|                         |                         |                         |
| .NameValue              |                         |                         |
|                         |                         |                         |
| .Name                   |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | The value of the name   |
|                         |                         |                         |
| .Product                |                         | value pair              |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .ItemSpecifics          |                         |                         |
|                         |                         |                         |
| .NameValueList          |                         |                         |
|                         |                         |                         |
| .NameValue              |                         |                         |
|                         |                         |                         |
| .Value                  |                         |                         |
+-------------------------+-------------------------+-------------------------+

Request Example
===============

::

    <GenerateQuote>
        <TranslationOptions>
            <Currency>EUR</Currency>
            <NotificationURL>
                    `https://www.example.com/
            </NotificationURL>
            <ServiceID>54</ServiceID>
            <SourceLanguage>
                <LanguageCode>en-uk</LanguageCode>
            </SourceLanguage>
            <TargetLanguages>
                <TargetLanguage>
                    <LanguageCode>it-it</LanguageCode>
                </TargetLanguage>
                    <TargetLanguage>
                        <LanguageCode>fr-fr</LanguageCode>
                    </TargetLanguage>
             </TargetLanguages>
        </TranslationOptions>
        <Products>
            <Product>
                <Title>The title of the item</Title>
                <PrimaryCategory>123</PrimaryCategory>
                <TopLevelCategory>1</TopLevelCategory>
                <CategoryPath>Clothing : Menswear : Shoes</CategoryPath>
                <Description>
                    <!--
                        This can be an XML block containing arbitrary, 
                        well formed sub elements.
                    -->

                    <Summary>
                        <![CDATA[
                                This is a summary it can contain HTML markup.
                                To tell the translation service to ignore some
                                text, wrap it in a
                                [do-not-translate]
                                do not translate
                                [/do-not-translate]
                                tag
                                ]]>

                    </Summary>
                    <Features>
                        <Feature1>Feature 1</Feature1>
                        <Feature2>Feature 2</Feature2>
                    </Features>        
                </Description>
                <SKUs>
                    <SKU>
                       <SKUNumber>1234</SKUNumber>
                      <ItemSpecifics>
                            <NameValueList>
                                <NameValue>
                                    <Name>Color</Name>
                                        <Value>White</Value>
                                </NameValue>
                                <NameValue>
                                    <Name>Size</Name>
                                    <Value>Large</Value>
                                </NameValue>
                            </NameValueList>
                      </ItemSpecifics>
                    </SKU>

                </SKUs>

            </Product>

        </Products>

    </GenerateQuote>


Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| Created                 | 201                     | The project was created |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     | This is probably        |
|                         |                         |                         |
|                         |                         | because of an invalid   |
|                         |                         |                         |
|                         |                         | parameter such as       |
|                         |                         |                         |
|                         |                         | service id.             |
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

The response body contains a quote for a project.

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| QuoteID                 | Integer                 | onDemand ID of the      |
|                         |                         |                         |
|                         |                         | Quote.                  |
+-------------------------+-------------------------+-------------------------+
| CreationDate            | String                  | String representing the |
|                         |                         |                         |
|                         |                         | date/time in the ISO    |
|                         |                         |                         |
|                         |                         | 8601 format. that the   |
|                         |                         |                         |
|                         |                         | project was created in  |
|                         |                         |                         |
|                         |                         | UTC.                    |
+-------------------------+-------------------------+-------------------------+
| AuthorizeURL            | String                  | URL to authorize the    |
|                         |                         |                         |
|                         |                         | project.  If AmountDue  |
|                         |                         |                         |
|                         |                         | > 0, this will be a     |
|                         |                         |                         |
|                         |                         | link to PayPal to pay   |
|                         |                         |                         |
|                         |                         | the translation.        |
|                         |                         |                         |
|                         |                         | Otherwise, see          |
|                         |                         |                         |
|                         |                         | AuthorizeProject        |
+-------------------------+-------------------------+-------------------------+
| RejectURL               | String                  | Use this                |
+-------------------------+-------------------------+-------------------------+
| ServiceID               | Integer                 | ID of Service           |
+-------------------------+-------------------------+-------------------------+
| SourceLanguage          | String                  | See LanguageCode in     |
|                         |                         |                         |
| .LanguageCode           |                         | glossary                |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Container containing    |
|                         |                         |                         |
|                         |                         | target languages.       |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | String                  | See LanguageCode in     |
|                         |                         |                         |
| .TargetLanguage         |                         | glossary                |
|                         |                         |                         |
| .LanguageCode           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TotalTranslations       | Integer                 | The number of           |
|                         |                         |                         |
|                         |                         | translations requested. |
|                         |                         |                         |
|                         |                         | For example, if the     |
|                         |                         |                         |
|                         |                         | merchant sends 5        |
|                         |                         |                         |
|                         |                         | products to be          |
|                         |                         |                         |
|                         |                         | translated into 3       |
|                         |                         |                         |
|                         |                         | languages, the value of |
|                         |                         |                         |
|                         |                         | TotalTranslations would |
|                         |                         |                         |
|                         |                         | be 15.                  |
+-------------------------+-------------------------+-------------------------+
| TranslationCredit       | Integer                 | Number of free          |
|                         |                         |                         |
|                         |                         | translations available  |
|                         |                         |                         |
|                         |                         | at the selected service |
|                         |                         |                         |
|                         |                         | level.                  |
+-------------------------+-------------------------+-------------------------+
| Currency                | String                  | Currency used to pay    |
|                         |                         |                         |
|                         |                         | for the project. See    |
|                         |                         |                         |
|                         |                         | glossary for list of    |
|                         |                         |                         |
|                         |                         | valid currencies.       |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TotalPrice              | Decimal                 | Total price that needs  |
|                         |                         |                         |
|                         |                         | to be paid. Exclude     |
|                         |                         |                         |
|                         |                         | translation credit.     |
+-------------------------+-------------------------+-------------------------+
| PrepaidCredit           | Decimal                 | If a merchant has a     |
|                         |                         |                         |
|                         |                         | positive credit balance |
|                         |                         |                         |
|                         |                         | with onDemand, it will  |
|                         |                         |                         |
|                         |                         | be reported here.       |
+-------------------------+-------------------------+-------------------------+
| AmountDue               | Decimal                 | TotalPrice -            |
|                         |                         | PrepaidCredit           |
+-------------------------+-------------------------+-------------------------+
|                         |                         |                         |
| Products                | Container               | Container of products   |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Container of SKU        |
|                         |                         |                         |
| .Product                |                         | elements                |
|                         |                         |                         |
| .SKUs                   |                         |                         | 
+-------------------------+-------------------------+-------------------------+
| Products                | Container               | Container of a SKU      |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | String                  | Item SKU                |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .SKUNumber              |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Products                | Integer                 | onDemand internal ID    |
|                         |                         |                         |
| .Product                |                         | for the listing         |
|                         |                         |                         |
| .AssetID                |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| DueDate                 | String                  | String representing     |
|                         |                         |                         |
|                         |                         | date/time (ISO 8601     |
|                         |                         |                         |
|                         |                         | format) that the        |
|                         |                         |                         |
|                         |                         | translation of the item |
|                         |                         |                         |
|                         |                         | is scheduled to be      |
|                         |                         |                         |
|                         |                         | completed in UTC        |
+-------------------------+-------------------------+-------------------------+

Response Example
================

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://</RejectURL>
        <ServiceID>54</ServiceID>
        <SourceLanguage>
        <LanguageCode>en-uk</LanguageCode>
        </SourceLanguage>
        <TargetLanguages>
                    <TargetLanguage>
                        <LanguageCode>it-it</LanguageCode>
                    </TargetLanguage>
                    <TargetLanguage>
                        <LanguageCode>fr-fr</LanguageCode>
                    </TargetLanguage>
        </TargetLanguages>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>1</TranslationCredit>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>

        <Products>
                <Product>
                    <AssetID>999</AssetID>
                    <SKUs>
                        <SKU>
                            <SKUNumber>123</SKUNumber>
                        </SKU>
                    </SKUs>
                    <DueDate>2014-02-11T10:22:46Z</DueDate> 
                </Product>
            </Products>
    </Quote>
