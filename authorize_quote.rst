===============
Authorize Quote
===============

=============  =================================
**Resource:**  /api/quote/<<quote id>>/authorize

**Method:**    POST
=============  =================================

This interface authorizes a quote.


Request Body
============

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| QuoteID                 | String                  | ID of the Quote         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| CreationDate            | String                  | String representing the |
|                         |                         |                         |
|                         |                         | date/time (ISO 8601)    |
|                         |                         |                         |
|                         |                         | that the project was    |
|                         |                         |                         |
|                         |                         | created in UTC.         |
+-------------------------+-------------------------+-------------------------+
| ServiceID               | Integer                 | ID of Service           |
+-------------------------+-------------------------+-------------------------+
| SourceLanguage.Language | String                  | See LanguageCode in     |
|                         |                         |                         |
| Code                    |                         | glossary                |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages         | Container               | Container containing    |
|                         |                         |                         |
|                         |                         | target languages.       |
+-------------------------+-------------------------+-------------------------+
| TargetLanguages.TargetL | String                  | See LanguageCode in     |
|                         |                         |                         |
| .TargetLangauages       |                         | glossary                |
|                         |                         |                         |
| .TargetLangauge         |                         |                         |
|                         |                         |                         |
| .LanaguageCode          |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TotalTranslations       | Integer                 | The number of           |
|                         |                         |                         |
|                         |                         | translations requested. |
|                         |                         |                         |
|                         |                         |  For example, if the    |
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

Request Example
===============

::

    <Quote>
        <QuoteID>795</QuoteID>
        <CreationDate>2014-06-25T16:39:07Z</CreationDate>
        <ServiceID>112</ServiceID>
        <SourceLanguage>
            <LanguageCode>en-gb</LanguageCode>
        </SourceLanguage>
        <TargetLanguages>
            <TargetLanguage>
                <LanguageCode>fr-fr</LanguageCode>
            </TargetLanguage>
            <TargetLanguage>
                <LanguageCode>it-it</LanguageCode>
            </TargetLanguage>
        </TargetLanguages>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>49984</TranslationCredit>
        <TotalCost>0.00</TotalCost>
        <PrepaidCredit>118.99</PrepaidCredit>
        <AmountDue>0.00</AmountDue>
        <Currency>EUR</Currency>
    </Quote>


Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| Created                 | 202                     | The approval was        |
|                         |                         |                         |
|                         |                         | accepted.               |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     | This could be that the  |
|                         |                         |                         |
|                         |                         | project doesn’t e       |
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
| Payment Required        | 402                     | The customer must pay   |
|                         |                         |                         |
|                         |                         | for the project before  |
|                         |                         |                         |
|                         |                         | authorizing it.         |
+-------------------------+-------------------------+-------------------------+
| Not Found               | 404                     | The URL does not relate |
|                         |                         |                         |
|                         |                         | to a project that the   |
|                         |                         |                         |
|                         |                         | merchant owns.          |
+-------------------------+-------------------------+-------------------------+
| Conflict                | 409                     | The quote is no longer  |
|                         |                         |                         |
|                         |                         | valid.  The response    |
|                         |                         |                         |
|                         |                         | body will return a      |
|                         |                         |                         |
|                         |                         | corrected quote that    |
|                         |                         |                         |
|                         |                         | can be approved.        |
+-------------------------+-------------------------+-------------------------+

Response Body
=============


+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comment                 |
+-------------------------+-------------------------+-------------------------+
| Status                  | String                  | Status of the quote.    |
|                         |                         |                         |
|                         |                         |  Authorized means that  |
|                         |                         |                         |
|                         |                         | the projects have been  |
|                         |                         |                         |
|                         |                         | paid for and the        |
|                         |                         |                         |
|                         |                         | project can start.      |
|                         |                         |                         |
|                         |                         |  Pending means that the |
|                         |                         |                         |
|                         |                         | merchant must execute a |
|                         |                         |                         |
|                         |                         | transaction to pay for  |
|                         |                         |                         |
|                         |                         | the project.  Look for  |
|                         |                         |                         |
|                         |                         | a PaymentURL for the    |
|                         |                         |                         |
|                         |                         | merchant to click       |
|                         |                         |                         |
|                         |                         | through.                |
+-------------------------+-------------------------+-------------------------+
| PaymentURL              | String                  | If additional funds are |
|                         |                         |                         |
|                         |                         | required, the status    |
|                         |                         |                         |
|                         |                         | code of 402 will be     |
|                         |                         |                         |
|                         |                         | returned and the        |
|                         |                         |                         |
|                         |                         | response will include a |
|                         |                         |                         |
|                         |                         | PaymentURL that         |
|                         |                         |                         |
|                         |                         | includes a link to a    |
|                         |                         |                         |
|                         |                         | paypal page.            |
+-------------------------+-------------------------+-------------------------+
| QuoteURL                | String                  | URL that can be used to |
|                         |                         |                         |
|                         |                         | check the status of the |
|                         |                         |                         |
|                         |                         | quote.  This is useful  |
|                         |                         |                         |
|                         |                         | for polling quotes that |
|                         |                         |                         |
|                         |                         | are externally paid     |
|                         |                         |                         |
|                         |                         | for.  See Get Quote.    |
+-------------------------+-------------------------+-------------------------+
| Projects                | Container               | A list of projects that |
|                         |                         |                         |
|                         |                         | have been generated by  |
|                         |                         |                         |
|                         |                         | this transaction.       |
+-------------------------+-------------------------+-------------------------+
| Projects.Project.Projec | Integer                 | onDemand Project ID for |
|                         |                         |                         |
| .Project                |                         | the project.            |
|                         |                         |                         |
| .ProjectID              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | String                  | A URL that can be       |
|                         |                         |                         |
| .Project                |                         | checked for the status  |
|                         |                         |                         |
| .ProjectURL             |                         | of the project.         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | String                  | String representing the |
|                         |                         |                         |
| .Project                |                         | date/time (ISO 8601)    |
|                         |                         |                         |
| .ProjectDueDate         |                         | that the project will   |
|                         |                         |                         |
|                         |                         | be completed by.        |
+-------------------------+-------------------------+-------------------------+
| Projects.               | Container               | List of products        |
|                         |                         |                         |
| .Project                |                         | included in the         |
|                         |                         |                         |
| .Products               |                         | product.                |
+-------------------------+-------------------------+-------------------------+
| Projects.               | String                  | Client supplied SKU     |
|                         |                         |                         |
| .Project                |                         | Number                  |
|                         |                         |                         |
| .Products               |                         |                         |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUNumber              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects.               | Integer                 | Internal onDemand ID    |
|                         |                         |                         |
| .Project                |                         | for this product.       |
|                         |                         |                         |
| .Products               |                         |                         |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .AssetID                |                         |                         |
+-------------------------+-------------------------+-------------------------+




Response Example
================


**No Payment Required**

::
    
    <QuoteAuthorization>
        <Status>Authorized</Status>
        <QuoteURL>https://</QuoteURL>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
                <Products>
                    <Product>
                        <AssetID>999</AssetID>
                        <SKUs>
                            <SKU>
                                <SKUNumber>123</SKUNumber>
                            </SKU>
                        </SKUs>
                    </Product>
                </Products>
            </Project>
        </Projects>
    </QuoteAuthorization>

**Payment Required**

::
    
    <QuoteAuthorization>
        <Status>Pending</Status>
        <PaymentURL>https://</PaymentURL>
        <QuoteURL>https://</QuoteURL>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
                <Products>
                    <Product>
                    <AssetID>999</AssetID>
                    <SKUs>
                        <SKU>
                            <SKUNumber>123</SKUNumber>
                        </SKU>
                    </SKUs>
                    </Product>
                </Products>
            </Project>
        </Projects>
    </QuoteAuthorization>


**Conflict**

See the response for Generate Quote