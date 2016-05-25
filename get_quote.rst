=========
Get Quote
=========

+---------------+----------------------------+
| **Resource:** | .. container:: notrans     |
|               |                            |
|               |    /api/quote/<<quote id>> |
+---------------+----------------------------+
| **Method:**   | .. container:: notrans     |
|               |                            |
|               |    GET                     |
+---------------+----------------------------+

Returns information about a quote.  This API is useful for polling

Arguments
=========

- **Quote ID:** The onDemand Quote ID.  You will receive this ID from :doc:`generate_quote`

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
|                         |                         | to a quote that the     |
|                         |                         |                         |
|                         |                         | account owns.           |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body contains information about the quote.

+-----------------------------+-------------------------+------------------------------------+
| Parameter                   | Type                    | Comment                            |
+=============================+=========================+====================================+
| .. container:: notrans      | Integer                 | onDemand ID for this quote.        |
|                             |                         |                                    |
|    QuoteID                  |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | String representing the            |
|                             |                         |                                    |
|    CreationDate             |                         | date/time in the ISO               |
|                             |                         |                                    |
|                             |                         | 8601 format. that the project      |
|                             |                         |                                    |
|                             |                         | was created in UTC.                |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Status of the quote.               |
|                             |                         |                                    |
|    Status                   |                         |  Authorized means that             |
|                             |                         |                                    |
|                             |                         | the projects have been             |
|                             |                         |                                    |
|                             |                         | paid for and the                   |
|                             |                         |                                    |
|                             |                         | project can start.                 |
|                             |                         |                                    |
|                             |                         |  Pending means that the            |
|                             |                         |                                    |
|                             |                         | merchant must execute a            |
|                             |                         |                                    |
|                             |                         | transaction to pay for             |
|                             |                         |                                    |
|                             |                         | the project.  Look for             |
|                             |                         |                                    |
|                             |                         | a PaymentURL for the               |
|                             |                         |                                    |
|                             |                         | merchant to click                  |
|                             |                         |                                    |
|                             |                         | through.                           |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | See :doc:`authorize_quote`         |
|                             |                         |                                    |
|    AuthorizeURL             |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | See :doc:`reject_quote`            |
|                             |                         |                                    |
|     RejectURL               |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Currency that the price            |
|                             |                         |                                    |
|    Currency                 |                         | is in. See glossary                |
|                             |                         |                                    |
|                             |                         | for list of valid                  |
|                             |                         |                                    |
|                             |                         | currencies.                        |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Decimal                 | Total price that needs             |
|                             |                         |                                    |
|    TotalCost                |                         | to be paid. Exclude                |
|                             |                         |                                    |
|                             |                         | translation credit.                |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Decimal                 | If a merchant has a                |
|                             |                         |                                    |
|    PrepaidCredit            |                         | positive credit balance            |
|                             |                         |                                    |
|                             |                         | with onDemand, it will             |
|                             |                         |                                    |
|                             |                         | be reported here.                  |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Decimal                 | TotalCost - Prepaid Credit         |
|                             |                         |                                    |
|    AmountDue                |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Tells onDemand how you would       |
|                             |                         |                                    |
|                             |                         | like to track file                 |
|                             |                         |                                    |
| TranslationAcceptanceMethod |                         | file acceptance. With the          |
|                             |                         |                                    |
|                             |                         | default method, "implicit,"        |
|                             |                         |                                    |
|                             |                         | we consider a file accepted        |
|                             |                         |                                    |
|                             |                         | when it is downloaded.             |
|                             |                         |                                    |
|                             |                         | With the optional "explicit"       |
|                             |                         |                                    |
|                             |                         | method we do not mark the          |
|                             |                         |                                    |
|                             |                         | file as accepted until we          |
|                             |                         |                                    |
|                             |                         | receive a request to the           |
|                             |                         |                                    |
|                             |                         | Accept Translation API,            |
|                             |                         |                                    |
|                             |                         | see :doc:`accept_file_translation`.|
|                             |                         |                                    |
|                             |                         | File acceptance/rejection          |
|                             |                         |                                    |
|                             |                         | is only intended to be used        |
|                             |                         |                                    |
|                             |                         | by API clients that do             |
|                             |                         |                                    |
|                             |                         | integrity checks on                |
|                             |                         |                                    |
|                             |                         | deliveries.                        |
|                             |                         |                                    |
|                             |                         | These methods are not              |
|                             |                         |                                    |
|                             |                         | intended to be used for            |
|                             |                         |                                    |
|                             |                         | subjective feedback on             |
|                             |                         |                                    |
|                             |                         | translation quality.               |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | A list of projects that            |
|                             |                         |                                    |
|    Projects                 |                         | have been generated by             |
|                             |                         |                                    |
|                             |                         | this transaction.                  |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | If the quote has been              |
|                             |                         |                                    |
|    Payments                 |                         | authorized, the payments           |
|                             |                         |                                    |
|                             |                         | section shows details              |
|                             |                         |                                    |
|                             |                         | about how the quote was            |
|                             |                         |                                    |
|                             |                         | paid.                              |
|                             |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | Contains information               |
|                             |                         |                                    |
|    Payments                 |                         | about an individual                |
|                             |                         |                                    |
|      .Payment               |                         | transaction                        |
|                             |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | PayPal, American                   |
|                             |                         |                                    |
|    Payments                 |                         | Express, Master Card,              |
|                             |                         |                                    |
|      .Payment               |                         | Visa, Prepaid, Purchase            |
|                             |                         |                                    |
|      .PaymentType           |                         | Order, Translation                 |
|                             |                         |                                    |
|                             |                         | Credit.                            |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | A string describing                |
|                             |                         |                                    |
|    Payments                 |                         | the funding source                 |
|                             |                         |                                    |
|      .Payment               |                         | such as Amex Charge to             |
|                             |                         |                                    |
|      .PaymentDescription    |                         | card ending in 1234                |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Decimal                 | Amount paid                        |
|                             |                         |                                    |
|    Payments                 |                         |                                    |
|                             |                         |                                    |
|      .Payment               |                         |                                    |
|                             |                         |                                    |
|      .PaymentAmount         |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Three letter currency              |
|                             |                         |                                    |
|    Payments                 |                         | code of the currency               |
|                             |                         |                                    |
|      .Payment               |                         | used in the transaction.           |
|                             |                         |                                    |
|      .PaymentCurrency       |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Integer                 | onDemand Project ID for            |
|                             |                         |                                    |
|    Projects                 |                         | the project.                       |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ProjectID             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | A URL that can be                  |
|                             |                         |                                    |
|    Projects                 |                         | checked for the status             |
|                             |                         |                                    |
|      .Project               |                         | of the project.                    |
|                             |                         |                                    |
|      .ProjectURL            |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | String representing the            |
|                             |                         |                                    |
|    Projects                 |                         | date/time (ISO 8601)               |
|                             |                         |                                    |
|      .Project               |                         | that the project will              |
|                             |                         |                                    |
|      .ProjectDueDate        |                         | be completed by.                   |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Integer                 | ID of Service                      |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ServiceID             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | List of products                   |
|                             |                         |                                    |
|    Projects                 |                         | included in the                    |
|                             |                         |                                    |
|      .Project               |                         | product.                           |
|                             |                         |                                    |
|      .Products              |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | List of SKUs under product         |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .Products              |                         |                                    |
|                             |                         |                                    |
|      .Product               |                         |                                    |
|                             |                         |                                    |
|      .SKUs                  |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | Contains a SKU                     |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .Products              |                         |                                    |
|                             |                         |                                    |
|      .Product               |                         |                                    |
|                             |                         |                                    |
|      .SKUs                  |                         |                                    |
|                             |                         |                                    |
|      .SKU                   |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Client supplied SKU Number         |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .Products              |                         |                                    |
|                             |                         |                                    |
|      .Product               |                         |                                    |
|                             |                         |                                    |
|      .SKUs                  |                         |                                    |
|                             |                         |                                    |
|      .SKU                   |                         |                                    |
|                             |                         |                                    |
|      .SKUNumber             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Integer                 | Internal onDemand ID               |
|                             |                         |                                    |
|    Projects                 |                         | for this product.                  |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .Products              |                         |                                    |
|                             |                         |                                    |
|      .Product               |                         |                                    |
|                             |                         |                                    |
|      .AssetID               |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Integer                 | Asset ID of the file.              |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .Files                 |                         |                                    |
|                             |                         |                                    |
|      .File                  |                         |                                    |
|                             |                         |                                    |
|      .AssetID               |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Original name of the file.         |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .Files                 |                         |                                    |
|                             |                         |                                    |
|      .File                  |                         |                                    |
|                             |                         |                                    |
|      .FileName              |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | See :doc:`list_files`              |
|                             |                         |                                    |
|    Projects                 |                         | for a list of file                 |
|                             |                         |                                    |
|      .Project               |                         | statuses.                          |
|                             |                         |                                    |
|      .Files                 |                         |                                    |
|                             |                         |                                    |
|      .File                  |                         |                                    |
|                             |                         |                                    |
|      .Status                |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | Container for a reference file.    |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFiles        |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFile         |                         |                                    |
|                             |                         |                                    |
|                             |                         |                                    |
|                             |                         |                                    |
|                             |                         |                                    |
|                             |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Integer                 | Asset ID of the file.              |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFiles        |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFile         |                         |                                    |
|                             |                         |                                    |
|      .AssetID               |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | Original name of the file.         |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFiles        |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFile         |                         |                                    |
|                             |                         |                                    |
|      .FileName              |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | URL where the file                 |
|                             |                         |                                    |
|    Projects                 |                         | can be downloaded.                 |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFiles        |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFile         |                         |                                    |
|                             |                         |                                    |
|      .URL                   |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | Empty element.                     |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFiles        |                         |                                    |
|                             |                         |                                    |
|      .ReferenceFile         |                         |                                    |
|                             |                         |                                    |
|      .TargetLanguages       |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | See LanguageCode in glossary       |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .SourceLanguage        |                         |                                    |
|                             |                         |                                    |
|      .LanguageCode          |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | Container               | Container containing               |
|                             |                         |                                    |
|    Projects                 |                         | target languages.                  |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .TargetLanguages       |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+
| .. container:: notrans      | String                  | See LanguageCode in glossary       |
|                             |                         |                                    |
|    Projects                 |                         |                                    |
|                             |                         |                                    |
|      .Project               |                         |                                    |
|                             |                         |                                    |
|      .TargetLanguages       |                         |                                    |
|                             |                         |                                    |
|      .TargetLanguage        |                         |                                    |
|                             |                         |                                    |
|      .LanguageCode          |                         |                                    |
+-----------------------------+-------------------------+------------------------------------+



Product-Based Quote Response Example
====================================

Quote is ready for payment.

::

   <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Pending</Status>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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
                    </Product>
                </Products>
            </Project>
        </Projects>
    </Quote>



Quote that has been authorized.

::

   <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Authorized</Status>
        <TotalCost>10.00</TotalCost>
        <Currency>EUR</Currency>
        <Payments>
            <Payment>
                <PaymentType>PayPal</PaymentType>
                <PaymentDescription>PayPal charge to buyer@example.com</PaymentDescription>
                <PaymentAmount>10.00</PaymentAmount>
                <PaymentCurrency>EURO</PaymentCurrency>
            </Payment>
        <Payments>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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
                    </Product>
                </Products>
            </Project>
        </Projects>
    </Quote>



File-Based Quote Response Example
====================================


**Quote is ready for payment**
::

   <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Pending</Status>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://…</RejectURL>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectName>Name of project</ProjectName>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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
                <Files>
                    <File>
                        <Status>Analyzed</Status>
                        <AssetID>999</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
            </Project>
        </Projects>
    </Quote>


**Quote has been authorized**
::

   <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Pending</Status>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://…</RejectURL>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>0.00</AmountDue>
        <Currency>EUR</Currency>
        <Payments>
            <Payment>
                <PaymentType>PayPal</PaymentType>
                <PaymentDescription>PayPal charge to buyer@example.com</PaymentDescription>
                <PaymentAmount>10.00</PaymentAmount>
                <PaymentCurrency>EURO</PaymentCurrency>
            </Payment>
        <Payments>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectName>Name of project</ProjectName>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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
                <Files>
                    <File>
                        <Status>Analyzed</Status>
                        <AssetID>999</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
            </Project>
        </Projects>
    </Quote>

**Price has not been calculated yet**

::

   <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>New</Status>
        <TotalCost/>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectName>Name of project</ProjectName>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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
                <Files>
                    <File>
                        <Status>Analyzing</Status>
                        <AssetID>999</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
            </Project>
        </Projects>
    </Quote>

**Quote contains a file that could not be parsed**

::

   <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Error</Status>
        <TotalCost>/>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectName>Name of project</ProjectName>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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
                <Files>
                    <File>
                        <Status>Analysis Failed</Status>
                        <AssetID>999</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
            </Project>
        </Projects>
    </Quote>
