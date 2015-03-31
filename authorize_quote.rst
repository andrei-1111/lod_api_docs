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

+-------------------------+-------------------------+-----------------------------------+
| Property                | Type                    | Comments                          |
+=========================+=========================+===================================+
| .. container:: notrans  | String                  | ID of the Quote                   |
|                         |                         |                                   |
|    QuoteID              |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | String representing the           |
|                         |                         |                                   |
|    CreationDate         |                         | date/time (ISO 8601)              |
|                         |                         |                                   |
|                         |                         | that the quote was                |
|                         |                         |                                   |
|                         |                         | created in UTC.                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Integer                 | The number of                     |
|                         |                         |                                   |
|    TotalTranslations    |                         | translations requested.           |
|                         |                         |                                   |
|                         |                         |  For example, if the              |
|                         |                         |                                   |
|                         |                         | merchant sends 5                  |
|                         |                         |                                   |
|                         |                         | products to be                    |
|                         |                         |                                   |
|                         |                         | translated into 3                 |
|                         |                         |                                   |
|                         |                         | languages, the value of           |
|                         |                         |                                   |
|                         |                         | TotalTranslations would           |
|                         |                         |                                   |
|                         |                         | be 15.                            |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Integer (optional)      | Number of free                    |
|                         |                         |                                   |
|    TranslationCredit    |                         | translations available            |
|                         |                         |                                   |
|                         |                         | at the selected service           |
|                         |                         |                                   |
|                         |                         | level.                            |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | Currency used to pay              |
|                         |                         |                                   |
|    Currency             |                         | for the project. See              |
|                         |                         |                                   |
|                         |                         | glossary for list of              |
|                         |                         |                                   |
|                         |                         | valid currencies.                 |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Decimal                 | Total price that needs            |
|                         |                         |                                   |
|    TotalCost            |                         | to be paid. Exclude               |
|                         |                         |                                   |
|                         |                         | translation credit.               |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Decimal                 | If a merchant has a               |
|                         |                         |                                   |
|    PrepaidCredit        |                         | positive credit balance           |
|                         |                         |                                   |
|                         |                         | with onDemand, it will            |
|                         |                         |                                   |
|                         |                         | be reported here.                 |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | If the site has been set up as a  |
|                         |                         |                                   |
|    InternalBillingCode  |                         | "provisioning" or "charge back"   |
|                         |                         |                                   |
|                         |                         | site, you have the option to be   |
|                         |                         |                                   |
|                         |                         | invoiced for transactions at a    |
|                         |                         |                                   |
|                         |                         | later date.  If the site is       |
|                         |                         |                                   |
|                         |                         | configured as a charge back site, |
|                         |                         |                                   |
|                         |                         | adding an InternalBillingCode to  |
|                         |                         |                                   |
|                         |                         | the request will automatically    |
|                         |                         |                                   |
|                         |                         | authorize the request and bill    |
|                         |                         |                                   |
|                         |                         | the transaction to a global       |
|                         |                         |                                   |
|                         |                         | purchase order. If the site has   |
|                         |                         |                                   |
|                         |                         | been configured to be a           |
|                         |                         |                                   |
|                         |                         | provisioning site,                |
|                         |                         |                                   |
|                         |                         | InternalBillingCode can be used   |
|                         |                         |                                   |
|                         |                         | optionally with                   |
|                         |                         |                                   |
|                         |                         | PurchaseOrderNumber to group      |
|                         |                         |                                   |
|                         |                         | transactions.                     |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | If the site has been set up as a  |
|                         |                         |                                   |
|    PurchaseOrderNumber  |                         | "provisioning" site, you have the |
|                         |                         |                                   |
|                         |                         | option to be invoiced for         |
|                         |                         |                                   |
|                         |                         | transactions at a later date. To  |
|                         |                         |                                   |
|                         |                         | do so, the authorization request  |
|                         |                         |                                   |
|                         |                         | has to contain a                  |
|                         |                         |                                   |
|                         |                         | PurchaseOrderNumber that matches  |
|                         |                         |                                   |
|                         |                         | a purchase order we have on file. |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
|                         |                         |                                   |
| .. container:: notrans  | Decimal                 | TotalCost -                       |
|                         |                         | PrepaidCredit                     |
|    AmountDue            |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  |                         |                                   |
|                         |                         |                                   |
|     Projects            | Integer                 | ProjectID of included             |
|                         |                         |                                   |
|       .Project          |                         | project                           |
|                         |                         |                                   |
|       .ProjectID        |                         |                                   |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  |                         |                                   |
|                         |                         |                                   |
|     Projects            | String                  | The name of the project           |
|                         |                         |                                   |
|       .Project          |                         |                                   |
|                         |                         |                                   |
|       .ProjectName      |                         |                                   |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  |                         |                                   |
|                         |                         |                                   |
|     Projects            | Integer                 | The ID of the service             |
|                         |                         |                                   |
|       .Project          |                         | used.                             |
|                         |                         |                                   |
|       .ServiceID        |                         |                                   |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  |                         |                                   |
|                         |                         |                                   |
|     Projects            | String                  | The language code of              |
|                         |                         |                                   |
|       .Project          |                         | source language.                  |
|                         |                         |                                   |
|       .SourceLanguage   |                         |                                   |
|                         |                         |                                   |
|       .LanguageCode     |                         |                                   |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  |                         |                                   |
|                         |                         |                                   |
|     Projects            | String                  | The language code of              |
|                         |                         |                                   |
|       .Project          |                         | a target language.                |
|                         |                         |                                   |
|       .TargetLanguages  |                         |                                   |
|                         |                         |                                   |
|       .TargetLanguage   |                         |                                   |
|                         |                         |                                   |
|       .LanguageCode     |                         |                                   |
|                         |                         |                                   |
|                         |                         |                                   |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  |                         |                                   |
|                         | Container               | Container of products             |
|    Projects             |                         |                                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Products          |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Container               | Container of SKU                  |
|                         |                         |                                   |
|    Projects             |                         | elements                          |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Products          |                         |                                   |
|                         |                         |                                   |
|      .Product           |                         |                                   |
|                         |                         |                                   |
|      .SKUs              |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Container               | Container of a SKU                |
|                         |                         |                                   |
|    Projects             |                         |                                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Products          |                         |                                   |
|                         |                         |                                   |
|      .Product           |                         |                                   |
|                         |                         |                                   |
|      .SKUs              |                         |                                   |
|                         |                         |                                   |
|      .SKU               |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | Item SKU                          |
|                         |                         |                                   |
|    Projects             |                         |                                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Products          |                         |                                   |
|                         |                         |                                   |
|      .Product           |                         |                                   |
|                         |                         |                                   |
|      .SKUs              |                         |                                   |
|                         |                         |                                   |
|      .SKU               |                         |                                   |
|                         |                         |                                   |
|      .SKUNumber         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Integer                 | onDemand internal ID              |
|                         |                         |                                   |
|    Projects             |                         | for the listing                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Products          |                         |                                   |
|                         |                         |                                   |
|      .Product           |                         |                                   |
|                         |                         |                                   |
|      .AssetID           |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | String representing               |
|                         |                         |                                   |
|    Projects             |                         | date/time (ISO 8601               |
|                         |                         |                                   |
|      .Project           |                         | format) that the                  |
|                         |                         |                                   |
|      .Products          |                         | translation of the item           |
|                         |                         |                                   |
|      .Product           |                         | is scheduled to be                |
|                         |                         |                                   |
|      .DueDate           |                         | completed in UTC                  |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Integer                 | Asset ID of the file.             |
|                         |                         |                                   |
|    Projects             |                         |                                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Files             |                         |                                   |
|                         |                         |                                   |
|      .File              |                         |                                   |
|                         |                         |                                   |
|      .AssetID           |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | Original name of the              |
|                         |                         |                                   |
|    Projects             |                         | file.                             |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .Files             |                         |                                   |
|                         |                         |                                   |
|      .File              |                         |                                   |
|                         |                         |                                   |
|      .FileName          |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Container               | Container for a                   |
|                         |                         |                                   |
|    Projects             |                         | reference file. A                 |
|                         |                         |                                   |
|      .Project           |                         | reference file is used            |
|                         |                         |                                   |
|      .ReferenceFiles    |                         | to inform the work that           |
|                         |                         |                                   |
|      .ReferenceFile     |                         | is being done. There is           |
|                         |                         |                                   |
|                         |                         | no charge for reference           |
|                         |                         |                                   |
|                         |                         | files.                            |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Integer                 | Asset ID of the                   |
|                         |                         |                                   |
|    Projects             |                         | reference file.                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFiles    |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFile     |                         |                                   |
|                         |                         |                                   |
|      .AssetID           |                         |                                   |
|                         |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | Original name of                  |
|                         |                         |                                   |
|    Projects             |                         | the file.                         |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFiles    |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFile     |                         |                                   |
|                         |                         |                                   |
|      .FileName          |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | String                  | URL where the file                |
|                         |                         |                                   |
|    Projects             |                         | can be downloaded.                |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFiles    |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFile     |                         |                                   |
|                         |                         |                                   |
|      .URL               |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
| .. container:: notrans  | Container               | Empty element.                    |
|                         |                         |                                   |
|    Projects             |                         |                                   |
|                         |                         |                                   |
|      .Project           |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFiles    |                         |                                   |
|                         |                         |                                   |
|      .ReferenceFile     |                         |                                   |
|                         |                         |                                   |
|      .TargetLanguages   |                         |                                   |
+-------------------------+-------------------------+-----------------------------------+
          

Pay As You Go Request Example          
=============================

::

    <Quote>
        <QuoteID>795</QuoteID>
        <CreationDate>2014-06-25T16:39:07Z</CreationDate>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>49984</TranslationCredit>
        <TotalCost>0.00</TotalCost>
        <PrepaidCredit>118.99</PrepaidCredit>
        <AmountDue>0.00</AmountDue>
        <Currency>EUR</Currency>
        <Projects>
                <Project>
                    <ProjectID>999</ProjectID>
                    <ProjectName>Name of project</ProjectName>
                    <ServiceID>54</ServiceID>
                    <SourceLanguage>
                        <LanguageCode>en-gb</LanguageCode>
                    </SourceLanguage>
                    <TargetLanguages>
                                <TargetLanguage>
                                    <LanguageCode>it-it</LanguageCode>
                                </TargetLanguage>
                                <TargetLanguage>
                                    <LanguageCode>fr-fr</LanguageCode>
                                </TargetLanguage>
                    </TargetLanguages>
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
                    <ReferenceFiles>
                        <ReferenceFile>
                            <AssetID>12345</AssetID>
                            <FileName>my-file.txt</FileName>
                            <URL>https://ondemand.liondemand.com/api/files/12345</URL>
                            <TargetLanguages />
                        </ReferenceFile>
                        <ReferenceFile>
                            <AssetID>12346</AssetID>
                            <FileName>my-file.txt</FileName>
                            <URL>https://ondemand.liondemand.com/api/files/12346</URL>
                            <TargetLanguages />
                        </ReferenceFile>
                    </ReferenceFiles>
                </Project>
        </Projects>
    </Quote>


Chargeback Request Example          
==========================

::

    <Quote>
        <QuoteID>795</QuoteID>
        <CreationDate>2014-06-25T16:39:07Z</CreationDate>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>49984</TranslationCredit>
        <TotalCost>0.00</TotalCost>
        <PrepaidCredit>118.99</PrepaidCredit>
        <AmountDue>0.00</AmountDue>
        <Currency>EUR</Currency>
        <InternalBillingCode>ABCD100001</InternalBillingCode>
        <Projects>
                <Project>
                    <ProjectID>999</ProjectID>
                    <ProjectName>Name of project</ProjectName>
                    <ServiceID>54</ServiceID>
                    <SourceLanguage>
                        <LanguageCode>en-gb</LanguageCode>
                    </SourceLanguage>
                    <TargetLanguages>
                                <TargetLanguage>
                                    <LanguageCode>it-it</LanguageCode>
                                </TargetLanguage>
                                <TargetLanguage>
                                    <LanguageCode>fr-fr</LanguageCode>
                                </TargetLanguage>
                    </TargetLanguages>
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
                    <ReferenceFiles>
                        <ReferenceFile>
                            <AssetID>12345</AssetID>
                            <FileName>my-file.txt</FileName>
                            <URL>https://ondemand.liondemand.com/api/files/12345</URL>
                            <TargetLanguages />
                        </ReferenceFile>
                        <ReferenceFile>
                            <AssetID>12346</AssetID>
                            <FileName>my-file.txt</FileName>
                            <URL>https://ondemand.liondemand.com/api/files/12346</URL>
                            <TargetLanguages />
                        </ReferenceFile>
                    </ReferenceFiles>
                </Project>
        </Projects>
    </Quote>

Provisioning Request Example          
============================

::

    <Quote>
        <QuoteID>795</QuoteID>
        <CreationDate>2014-06-25T16:39:07Z</CreationDate>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>49984</TranslationCredit>
        <TotalCost>0.00</TotalCost>
        <PrepaidCredit>118.99</PrepaidCredit>
        <AmountDue>0.00</AmountDue>
        <Currency>EUR</Currency>
        <PurchaseOrderNumber>001-005-100</PurchaseOrderNumber>
        <InternalBillingCode>ABCD100001</InternalBillingCode>
        <Projects>
                <Project>
                    <ProjectID>999</ProjectID>
                    <ProjectName>Name of project</ProjectName>
                    <ServiceID>54</ServiceID>
                    <SourceLanguage>
                        <LanguageCode>en-gb</LanguageCode>
                    </SourceLanguage>
                    <TargetLanguages>
                                <TargetLanguage>
                                    <LanguageCode>it-it</LanguageCode>
                                </TargetLanguage>
                                <TargetLanguage>
                                    <LanguageCode>fr-fr</LanguageCode>
                                </TargetLanguage>
                    </TargetLanguages>
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
                    <ReferenceFiles>
                        <ReferenceFile>
                            <AssetID>12345</AssetID>
                            <FileName>my-file.txt</FileName>
                            <URL>https://ondemand.liondemand.com/api/files/12345</URL>
                            <TargetLanguages />
                        </ReferenceFile>
                        <ReferenceFile>
                            <AssetID>12346</AssetID>
                            <FileName>my-file.txt</FileName>
                            <URL>https://ondemand.liondemand.com/api/files/12346</URL>
                            <TargetLanguages />
                        </ReferenceFile>
                    </ReferenceFiles>
                </Project>
        </Projects>
    </Quote>




Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Accepted                | 202                     | The approval was        |
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
| 308                     | Invalid Purchase Order  | The purchase order      |
|                         |                         |                         |
|                         |                         | number submitted is     |
|                         |                         |                         |
|                         |                         | either invalid or the   |
|                         |                         |                         |
|                         |                         | purchase order has an   |
|                         |                         |                         |
|                         |                         | insufficient remaining  |
|                         |                         |                         |
|                         |                         | balance.                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 309                     | Buyer not authorized    | This buyer is not       |
|                         |                         |                         |
|                         | for purchase orders.    | authorized to use       |
|                         |                         |                         |
|                         |                         | purchase orders.        |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 310                     | Improperly configured   | The billing information |
|                         |                         |                         |
|                         | site billing information| on this site is not     |
|                         |                         |                         |
|                         |                         | properly configured.    |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+

