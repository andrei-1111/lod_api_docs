===============
Authorize Quote
===============

+---------------+--------------------------------------+
| **Resource:** | .. container:: notrans               |
|               |                                      |
|               |    /api/quote/<<quote id>>/authorize |
+---------------+--------------------------------------+
| **Method:**   | .. container:: notrans               |
|               |                                      |
|               |    POST                              |
+---------------+--------------------------------------+

This interface authorizes a quote.  Only quotes with a status of "Pending" can be authorized.



Request Body
============

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | String                  | ID of the Quote         |
|                         |                         |                         |
|    QuoteID              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing the |
|                         |                         |                         |
|    CreationDate         |                         | date/time (ISO 8601)    |
|                         |                         |                         |
|                         |                         | that the project was    |
|                         |                         |                         |
|                         |                         | created in UTC.         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | ID of Service           |
|                         |                         |                         |
|    ServiceID            |                         |                         |
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
|      .TargetLangauge    |                         |                         |
|                         |                         |                         |
|      .LanaguageCode     |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | The number of           |
|                         |                         |                         |
|    TotalTranslations    |                         | translations requested. |
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
| .. container:: notrans  | Integer                 | Number of free          |
|                         |                         |                         |
|    TranslationCredit    |                         | translations available  |
|                         |                         |                         |
|                         |                         | at the selected service |
|                         |                         |                         |
|                         |                         | level.                  |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Currency used to pay    |
|                         |                         |                         |
|    Currency             |                         | for the project. See    |
|                         |                         |                         |
|                         |                         | glossary for list of    |
|                         |                         |                         |
|                         |                         | valid currencies.       |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | Total price that needs  |
|                         |                         |                         |
|    TotalPrice           |                         | to be paid. Exclude     |
|                         |                         |                         |
|                         |                         | translation credit.     |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | If a merchant has a     |
|                         |                         |                         |
|    PrepaidCredit        |                         | positive credit balance |
|                         |                         |                         |
|                         |                         | with onDemand, it will  |
|                         |                         |                         |
|                         |                         | be reported here.       |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | TotalPrice -            |
|                         |                         | PrepaidCredit           |
|    AmountDue            |                         |                         |
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
+=========================+=========================+=========================+
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
| Method not Allowed      | 405                     | The Quote is not ready  |
|                         |                         |                         |
|                         |                         | to be paid because the  |
|                         |                         |                         |
|                         |                         | price is not set.       |
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
+=========================+=========================+=========================+
| .. container:: notrans  | String                  | Status of the quote.    |
|                         |                         |                         |
|    Status               |                         |  Authorized means that  |
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
| .. container:: notrans  | String                  | If additional funds are |
|                         |                         |                         |
|    PaymentURL           |                         | required, the status    |
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
| .. container:: notrans  | String                  | URL that can be used to |
|                         |                         |                         |
|    QuoteURL             |                         | check the status of the |
|                         |                         |                         |
|                         |                         | quote.  This is useful  |
|                         |                         |                         |
|                         |                         | for polling quotes that |
|                         |                         |                         |
|                         |                         | are externally paid     |
|                         |                         |                         |
|                         |                         | for.  See Get Quote.    |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | A list of projects that |
|                         |                         |                         |
|    Projects             |                         | have been generated by  |
|                         |                         |                         |
|                         |                         | this transaction.       |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | onDemand Project ID for |
|                         |                         |                         |
|    Projects             |                         | the project.            |
|                         |                         |                         |
|      .Project           |                         |                         |
|                         |                         |                         |
|      .ProjectID         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | A URL that can be       |
|                         |                         |                         |
|    Projects             |                         | checked for the status  |
|                         |                         |                         |
|      .Project           |                         | of the project.         |
|                         |                         |                         |
|      .ProjectURL        |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing the |
|                         |                         |                         |
|    Projects             |                         | date/time (ISO 8601)    |
|                         |                         |                         |
|      .Project           |                         | that the project will   |
|                         |                         |                         |
|      .ProjectDueDate    |                         | be completed by.        |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | List of products        |
|                         |                         |                         |
|    Projects             |                         | included in the         |
|                         |                         |                         |
|      .Project           |                         | product.                |
|                         |                         |                         |
|      .Products          |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Client supplied SKU     |
|                         |                         |                         |
|    Projects             |                         | Number                  |
|                         |                         |                         |
|      .Project           |                         |                         |
|                         |                         |                         |
|      .Products          |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKUNumber         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | Internal onDemand ID    |
|                         |                         |                         |
|    Projects             |                         | for this product.       |
|                         |                         |                         |
|      .Project           |                         |                         |
|                         |                         |                         |
|      .Products          |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .AssetID           |                         |                         |
+-------------------------+-------------------------+-------------------------+




Product-Based Quote Authorization Response Example
==================================================


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

File-Based Quote Authorization Response Example
==================================================


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
                <Files>
                    <File>
                        <Status>Analyzed</Status>
                        <AssetID>123</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
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
                <Files>
                    <File>
                        <Status>Analyzed</Status>
                        <AssetID>123</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
            </Project>
        </Projects>
    </QuoteAuthorization>

**Parsing Failed**

If one or more of the files submitted for this quote did not parse properly

::

    <QuoteAuthorization>
        <Status>Error</Status>
        <QuoteURL>https://</QuoteURL>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
                <Files>
                    <File>
                        <Status>Analyzed</Status>
                        <AssetID>123</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                    <File>
                        <Status>Analysis Failed</Status>
                        <AssetID>124</AssetID>
                        <FileName>example2.txt</FileName>
                    </File>
                </Files>
            </Project>
        </Projects>
        <Error>
            <ReasonCode>307</ReasonCode>
            <SimpleMessage>Parsing Failed</SimpleMessage>
            <DetailedMessage>
                            One or more of the files                      
                            encountered a parsing   
                            error. This quote is    
                            invalid.
            </DetailedMessage>
        </Error>                            
    </QuoteAuthorization>

Errors
======
If Authorize Quote encountered an error, the response will contain an Error element consisting of
a ReasonCode, SimpleMessage, and DetailedMessage elements. See :doc:`error_handling` for more 
information.  The most common error will be related to a conflict (HTTP status code 409), which 
happens when the quote information submitted does not match the information within the onDemand 
service.

+-------------------------+-------------------------+-------------------------+
| ReasonCode              | SimpleMessage           | DetailedMessage         |
+=========================+=========================+=========================+
| 300                     | Miscellaneous error     | A miscellaneous or      |
|                         |                         |                         |
|                         |                         | unexpected error        |
|                         |                         |                         |
|                         |                         | has occured.            |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 301                     | The number of available | When this quote was     |
|                         |                         |                         |
|                         | translation credits has | created, the number of  |
|                         |                         |                         |
|                         | changed.                | available translation   |
|                         |                         |                         |
|                         |                         | credit was different    |
|                         |                         |                         |
|                         |                         | than are available now. |
+-------------------------+-------------------------+-------------------------+
| 302                     | The amount of prepaid   | When this quote was     |
|                         |                         |                         |
|                         | available pre-paid      | created, the amount of  |
|                         |                         |                         |
|                         | has changed.            | prepaid credit was      |
|                         |                         |                         |
|                         |                         | different than it is    |
|                         |                         |                         |
|                         |                         | now.                    |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 303                     | Wrong quote ID          | The QuoteID in the      |
|                         |                         |                         |
|                         |                         | request body does not   |
|                         |                         |                         |
|                         |                         | match what was in the   |
|                         |                         |                         |
|                         |                         | URL.                    |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 304                     | Wrong language options  | The source or target    |
|                         |                         |                         |
|                         |                         | languages are different |
|                         |                         |                         |
|                         |                         | that when the quote     |
|                         |                         |                         |
|                         |                         | was created.            |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 305                     | Price change            | The price has changed.  |
|                         |                         |                         |
|                         |                         | This could be because   |
|                         |                         |                         |
|                         |                         | less credit is available|
|                         |                         |                         |
|                         |                         | or it could be because  |
|                         |                         |                         |
|                         |                         | the information sent    |
|                         |                         |                         |
|                         |                         | in the quote has been   |
|                         |                         |                         |
|                         |                         | been altered.           |
+-------------------------+-------------------------+-------------------------+
| 306                     | Quote Not Ready         | The quote is not yet in |
|                         |                         |                         |
|                         |                         | a pending state so      |
|                         |                         |                         |
|                         |                         | it cannot be authorized.|
|                         |                         |                         |
|                         |                         | This reason code will   |
|                         |                         |                         |
|                         |                         | be accompanied by an    |
|                         |                         |                         |
|                         |                         | HTTP status code of 405.|
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 307                     | Parsing Failed          | One or more of the files|
|                         |                         |                         |
|                         |                         | encountered a parsing   |
|                         |                         |                         |
|                         |                         | error. This quote is    |
|                         |                         |                         |
|                         |                         | invalid.                |
+-------------------------+-------------------------+-------------------------+

