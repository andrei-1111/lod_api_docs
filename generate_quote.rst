==============
Generate Quote
==============

+-----------------+------------------------+
| **Resource:**   | .. container:: notrans |
|                 |                        |
|                 |    /api/quote/generate |
+-----------------+------------------------+
| **Method:**     | .. container:: notrans |
|                 |                        |
|                 |    POST                |
+-----------------+------------------------+

This interface is used to generate a quote.  A quote can contain multiple projects.

Quotes can be generated using different inputs:

- Product elements, which are are inserted into the generate quote request
- Files that were uploading using the :doc:`add_file` API.
- Projects that were added using the :doc:`add_project` API.  These projects contain either files or products.  The advantage of generating a quote out of individual projects is that it allows you more flexibility.  For example, you can have different source languages, target languages, and even services.

The API client should use an API key set associated with a customer (merchant) account when submitting and retrieving projects on behalf of that customer.  This will establish ownership of that project for access control and also attribute transactions to individual customer accounts. The API client can create an customer account using the :doc:`create_account` API.




Request Body
============


+-----------------------------------+-------------------------+------------------------------------+
| Parameter                         | Type                    | Comments                           |
+===================================+=========================+====================================+
| .. container:: notrans            | Container               | Contains information               |
|                                   |                         |                                    |
|    TranslationOptions             |                         | specifying the                     |
|                                   |                         |                                    |
|                                   |                         | translation project.               |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | String representing                |
|                                   |                         |                                    |
|  TranslationOptions               |                         | currency that the                  |
|                                   |                         |                                    |
|    .Currency                      |                         | merchant wishes to pay             |
|                                   |                         |                                    |
|                                   |                         | with. See glossary for             |
|                                   |                         |                                    |
|                                   |                         | list of valid                      |
|                                   |                         |                                    |
|                                   |                         | currencies.                        |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String (optional)       | When a project is                  |
|                                   |                         |                                    |
|    TranslationOptions             |                         | complete, the API                  |
|                                   |                         |                                    |
|     .NotifyCompleteURL            |                         | will send a POST                   |
|                                   |                         |                                    |
|                                   |                         | request to this URL. See the       |
|                                   |                         |                                    |
|                                   |                         | :doc:`notify_project_complete`     |
|                                   |                         |                                    |
|                                   |                         | API documentation for the          |
|                                   |                         |                                    |
|                                   |                         | structure of the post body.        |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String (optional)       | When the quote has been            |
|                                   |                         |                                    |
|    TranslationOptions             |                         | priced and is ready for            |
|                                   |                         |                                    |
|     .NotifyQuoteReadyURL          |                         | purchase, the API will             |
|                                   |                         |                                    |
|                                   |                         | send a post request to             |
|                                   |                         |                                    |
|                                   |                         | this URL.                          |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String (optional)       | When the quote has been            |
|                                   |                         |                                    |
|    TranslationOptions             |                         | paid, the API will send            |
|                                   |                         |                                    |
|      .NotifyQuotePaidURL          |                         | a POST to this URL.                |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Integer                 | Numeric service code               |
|                                   |                         |                                    |
|    TranslationOptions             |                         | for the translation                |
|                                   |                         |                                    |
|      .ServiceID                   |                         | service.  The service              |
|                                   |                         |                                    |
|                                   |                         | defines a set of                   |
|                                   |                         |                                    |
|                                   |                         | options such as machine            |
|                                   |                         |                                    |
|                                   |                         | translation with post              |
|                                   |                         |                                    |
|                                   |                         | edit on the title and              |
|                                   |                         |                                    |
|                                   |                         | raw machine translation            |
|                                   |                         |                                    |
|                                   |                         | on the body.  This                 |
|                                   |                         |                                    |
|                                   |                         | element is optional                |
|                                   |                         |                                    |
|                                   |                         | and ignored for quotes             |
|                                   |                         |                                    |
|                                   |                         | that are generated from            |
|                                   |                         |                                    |
|                                   |                         | projects.                          |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Contains 1 source                  |
|                                   |                         |                                    |
|    TranslationOptions             |                         | language. This                     |
|                                   |                         |                                    |
|      .SourceLanguage              |                         | element is optional                |
|                                   |                         |                                    |
|                                   |                         | and ignored for quotes             |
|                                   |                         |                                    |
|                                   |                         | that are generated from            |
|                                   |                         |                                    |
|                                   |                         | prjoects.                          |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | See LanguageCode in glossary       |
|                                   |                         |                                    |
|    TranslationOptions             |                         |                                    |
|                                   |                         |                                    |
|      .SourceLanguage              |                         |                                    |
|                                   |                         |                                    |
|      .LanguageCode                |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String (optional)       | Special instructions for use       |
|                                   |                         |                                    |
|    TranslationOptions             |                         | by translators.                    |
|                                   |                         |                                    |
|      .SpecialInstructions         |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Contains 1 or more                 |
|                                   |                         |                                    |
|    TranslationOptions             |                         | target languages. This             |
|                                   |                         |                                    |
|      .TargetLanguages             |                         | element is optional                |
|                                   |                         |                                    |
|                                   |                         | and ignored for quotes             |
|                                   |                         |                                    |
|                                   |                         | that are generated from            |
|                                   |                         |                                    |
|                                   |                         | projects.                          |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | See LanguageCode in glossary       |
|                                   |                         |                                    |
|    TranslationOptions             |                         |                                    |
|                                   |                         |                                    |
|      .TargetLanguages             |                         |                                    |
|                                   |                         |                                    |
|      .TargetLanguage              |                         |                                    |
|                                   |                         |                                    |
|      .LanguageCode                |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String (optional)       | Tells onDemand how you would       |
|                                   |                         |                                    |
|    TranslationOptions             |                         | like to track file                 |
|                                   |                         |                                    |
|      .TranslationAcceptanceMethod |                         | acceptance. With the               |
|                                   |                         |                                    |
|                                   |                         | default method, "implicit,"        |
|                                   |                         |                                    |
|                                   |                         | we consider a file accepted        |
|                                   |                         |                                    |
|                                   |                         | when it is downloaded.             |
|                                   |                         |                                    |
|                                   |                         | With the optional "explicit"       |
|                                   |                         |                                    |
|                                   |                         | method we do not mark the          |
|                                   |                         |                                    |
|                                   |                         | file as accepted until we          |
|                                   |                         |                                    |
|                                   |                         | receive a request to the           |
|                                   |                         |                                    |
|                                   |                         | Accept Translation API,            |
|                                   |                         |                                    |
|                                   |                         | see :doc:`accept_file_translation`.|
|                                   |                         |                                    |
|                                   |                         | File acceptance/rejection          |
|                                   |                         |                                    |
|                                   |                         | is only intended to be used        |
|                                   |                         |                                    |
|                                   |                         | by API clients that do             |
|                                   |                         |                                    |
|                                   |                         | integrity checks on                |
|                                   |                         |                                    |
|                                   |                         | deliveries.                        |
|                                   |                         |                                    |
|                                   |                         | These methods are not              |
|                                   |                         |                                    |
|                                   |                         | intended to be used for            |
|                                   |                         |                                    |
|                                   |                         | subjective feedback on             |
|                                   |                         |                                    |
|                                   |                         | translation quality.               |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | List                    | List of Product                    |
|                                   |                         |                                    |
|    Products                       |                         | Elements. Products                 |
|                                   |                         |                                    |
|                                   |                         | are only allowed as                |
|                                   |                         |                                    |
|                                   |                         | input if the service               |
|                                   |                         |                                    |
|                                   |                         | supports products.                 |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | The title of the product           |
|                                   |                         |                                    |
|    Products                       |                         |                                    |
|                                   |                         |                                    |
|      .Product                     |                         |                                    |
|                                   |                         |                                    |
|      .Title                       |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Integer                 | ID of the product’s                |
|                                   |                         |                                    |
|    Products                       |                         |                                    |
|                                   |                         | primary category                   |
|      .Product                     |                         |                                    |
|                                   |                         |                                    |
|      .PrimaryCategory             |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Integer                 | ID of the top level                |
|                                   |                         |                                    |
|    Products                       |                         | category that the                  |
|                                   |                         |                                    |
|      .Product                     |                         | product sits in                    |
|                                   |                         |                                    |
|      .TopLevelCategory            |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | Delimited string                   |
|                                   |                         |                                    |
|    Products                       |                         | showing the path                   |
|                                   |                         |                                    |
|      .Product                     |                         | through the category               |
|                                   |                         |                                    |
|      .CategoryPath                |                         | hierarchy to the                   |
|                                   |                         |                                    |
|                                   |                         | primary category.  This            |
|                                   |                         |                                    |
|                                   |                         | is mainly for                      |
|                                   |                         |                                    |
|                                   |                         | contextual information             |
|                                   |                         |                                    |
|                                   |                         | for the translators.               |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | The description of the             |
|                                   |                         |                                    |
|    Products                       |                         | item.  This element can            |
|                                   |                         |                                    |
|      .Product                     |                         | contain sub-elements.              |
|                                   |                         |                                    |
|      .Description                 |                         | HTML that is not well              |
|                                   |                         |                                    |
|                                   |                         | formed XML should be               |
|                                   |                         |                                    |
|                                   |                         | wrapped in CDATA tags.             |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Contains a SKU elements            |
|                                   |                         |                                    |
|    Products                       |                         |                                    |
|                                   |                         |                                    |
|      .Product                     |                         |                                    |
|                                   |                         |                                    |
|      .SKUs                        |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Contains a SKU Number              |
|                                   |                         |                                    |
|    Products                       |                         | and a list of                      |
|                                   |                         |                                    |
|      .Product                     |                         | ItemSpecifics that are             |
|                                   |                         |                                    |
|      .SKUs                        |                         | relevant to the SKU                |
|                                   |                         |                                    |
|      .SKU                         |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | SKU Number                         |
|                                   |                         |                                    |
|    Products                       |                         |                                    |
|                                   |                         |                                    |
|      .Product                     |                         |                                    |
|                                   |                         |                                    |
|      .SKUs                        |                         |                                    |
|                                   |                         |                                    |
|      .SKU                         |                         |                                    |
|                                   |                         |                                    |
|      .SKUNumber                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Contains elements                  |
|                                   |                         |                                    |
|    Products                       |                         | representing                       |
|                                   |                         |                                    |
|      .Product                     |                         | specifications.                    |
|                                   |                         |                                    |
|      .SKUs                        |                         |                                    |
|                                   |                         |                                    |
|      .SKU                         |                         |                                    |
|                                   |                         |                                    |
|      .ItemSpecifics               |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Contains elements                  |
|                                   |                         |                                    |
|    Products                       |                         | representing name-value            |
|                                   |                         |                                    |
|      .Product                     |                         | pairs                              |
|                                   |                         |                                    |
|      .SKUs                        |                         |                                    |
|                                   |                         |                                    |
|      .SKU                         |                         |                                    |
|                                   |                         |                                    |
|      .ItemSpecifics               |                         |                                    |
|                                   |                         |                                    |
|      .ItemSepecific               |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | The name of the name value pair    |
|                                   |                         |                                    |
|    Products                       |                         |                                    |
|                                   |                         |                                    |
|      .Product                     |                         |                                    |
|                                   |                         |                                    |
|      .SKUs                        |                         |                                    |
|                                   |                         |                                    |
|      .SKU                         |                         |                                    |
|                                   |                         |                                    |
|      .ItemSpecifics               |                         |                                    |
|                                   |                         |                                    |
|      .ItemSpecific                |                         |                                    |
|                                   |                         |                                    |
|      .Name                        |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | String                  | The name of the name value pair    |
|                                   |                         |                                    |
|    Products                       |                         |                                    |
|                                   |                         |                                    |
|      .Product                     |                         |                                    |
|                                   |                         |                                    |
|      .SKUs                        |                         |                                    |
|                                   |                         |                                    |
|      .SKU                         |                         |                                    |
|                                   |                         |                                    |
|      .ItemSpecifics               |                         |                                    |
|                                   |                         |                                    |
|      .ItemSpecific                |                         |                                    |
|                                   |                         |                                    |
|      .Value                       |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | A collection of file               |
|                                   |                         |                                    |
|    Files                          |                         | elements. The files                |
|                                   |                         |                                    |
|                                   |                         | referenced need to                 |
|                                   |                         |                                    |
|                                   |                         | supported by the                   |
|                                   |                         |                                    |
|                                   |                         | selected service.                  |
|                                   |                         |                                    |
|                                   |                         | See :doc:`list_services`           |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | A file is described                |
|                                   |                         |                                    |
|    Files                          |                         | with a AssetID of a                |
|                                   |                         |                                    |
|      .File                        |                         | previously uploaded file           |
|                                   |                         |                                    |
|                                   |                         | (see :doc:`add_file`)              |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Integer                 | AssetID of previously              |
|                                   |                         |                                    |
|    Files                          |                         | uploaded file. Note:               |
|                                   |                         |                                    |
|      .File                        |                         | the file type needs to             |
|                                   |                         |                                    |
|      .AssetID                     |                         | be consistent with the             |
|                                   |                         |                                    |
|                                   |                         | valid file types for               |
|                                   |                         |                                    |
|                                   |                         | the service. Also,                 |
|                                   |                         |                                    |
|                                   |                         | a file cannot be                   |
|                                   |                         |                                    |
|                                   |                         | associated with more               |
|                                   |                         |                                    |
|                                   |                         | that one quote.                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Container               | Container for a reference file.    |
|                                   |                         |                                    |
|    ReferenceFiles                 |                         | A reference file is used to        |
|                                   |                         |                                    |
|      .ReferenceFile               |                         | inform the work that is being      |
|                                   |                         |                                    |
|                                   |                         | done.  There is no charge for      |
|                                   |                         |                                    |
|                                   |                         | reference files. Reference         |
|                                   |                         |                                    |
|                                   |                         | are always optional.               |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+
| .. container:: notrans            | Integer                 | Asset ID of the reference file.    |
|                                   |                         |                                    |
|    ReferenceFiles                 |                         |                                    |
|                                   |                         |                                    |
|      .ReferenceFile               |                         |                                    |
|                                   |                         |                                    |
|      .AssetID                     |                         |                                    |
|                                   |                         |                                    |
|                                   |                         |                                    |
+-----------------------------------+-------------------------+------------------------------------+


Product Request Example
=======================

::

    <GenerateQuote>
        <TranslationOptions>
            <Currency>EUR</Currency>
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
                            <ItemSpecific>
                                <Name>Color</Name>
                                <Value>White</Value>
                            </ItemSpecific>
                            <ItemSpecific>
                                <Name>Size</Name>
                                <Value>Large</Value>
                            </ItemSpecific>
                      </ItemSpecifics>
                    </SKU>
                </SKUs>
            </Product>
        </Products>
        <ReferenceFiles>
            <ReferenceFile>
                <AssetID>12345</AssetID>
            </ReferenceFile>
            <ReferenceFile>
                <AssetID>12346</AssetID>
            </ReferenceFile>
        </ReferenceFiles>
    </GenerateQuote>


File Request Example
====================

::

    <GenerateQuote>
        <TranslationOptions>
            <Currency>EUR</Currency>
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
        </TranslationOptions>
        <Files>
            <File>
                <AssetID>123456</AssetID>
            </File>
        </Files>
        <ReferenceFiles>
            <ReferenceFile>
                <AssetID>12345</AssetID>
            </ReferenceFile>
            <ReferenceFile>
                <AssetID>12346</AssetID>
            </ReferenceFile>
        </ReferenceFiles>
    </GenerateQuote>


Project Request Example
=======================

::

    <GenerateQuote>
        <TranslationOptions>
            <Currency>EUR</Currency>
        </TranslationOptions>
        <Projects>
            <Project>
                <ProjectID>123456</ProjectID>
            </Project>
        </Projects>
    </GenerateQuote>





Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Created                 | 201                     | The project was created |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     | This is probably        |
|                         |                         |                         |
|                         |                         | because of a malformed  |
|                         |                         |                         |
|                         |                         | request body.           |
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
| Conflict                | 409                     | This is probably        |
|                         |                         |                         |
|                         |                         | because of an invalid   |
|                         |                         |                         |
|                         |                         | parameter such as the   |
|                         |                         |                         |
|                         |                         | wrong service id or     |
|                         |                         |                         |
|                         |                         | incompatible file types.|
+-------------------------+-------------------------+-------------------------+


Response Body
=============

The response body contains a quote for a project. Please note: the response may
not contain a price.  If the submitted files

+---------------------------+-------------------------+-------------------------+
| Property                  | Type                    | Comments                |
+===========================+=========================+=========================+
| .. container:: notrans    | Integer                 | onDemand ID of the      |
|                           |                         |                         |
|    QuoteID                |                         | Quote.                  |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | String representing the |
|                           |                         |                         |
|    CreationDate           |                         | date/time in the ISO    |
|                           |                         |                         |
|                           |                         | 8601 format. that the   |
|                           |                         |                         |
|                           |                         | project was created in  |
|                           |                         |                         |
|                           |                         | UTC.                    |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | The status of the quote.|
|                           |                         |                         |
|    Status                 |                         | "Pending" means that the|
|                           |                         |                         |
|                           |                         | source content has been |
|                           |                         |                         |
|                           |                         | analyzed and the        |
|                           |                         |                         |
|                           |                         | project(s) has/have     |
|                           |                         |                         |
|                           |                         | been priced.            |
|                           |                         |                         |
|                           |                         | "Analyzing" means that  |
|                           |                         |                         |
|                           |                         | the price is still      |
|                           |                         |                         |
|                           |                         | being determined and    |
|                           |                         |                         |
|                           |                         | the client should       |
|                           |                         |                         |
|                           |                         | call :doc:`get_quote`   |
|                           |                         |                         |
|                           |                         | later to check on the   |
|                           |                         |                         |
|                           |                         | status.                 |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | URL to authorize the    |
|                           |                         |                         |
|    AuthorizeURL           |                         | quote.  See             |
|                           |                         |                         |
|                           |                         | :doc:`authorize_quote`  |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | Use this to reject the  |
|                           |                         |                         |
|    RejectURL              |                         | quote. See              |
|                           |                         | :doc:`reject_quote`     |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Integer                 | The number of           |
|                           |                         |                         |
|    TotalTranslations      |                         | translations requested. |
|                           |                         |                         |
|                           |                         | For example, if the     |
|                           |                         |                         |
|                           |                         | merchant sends 5        |
|                           |                         |                         |
|                           |                         | products to be          |
|                           |                         |                         |
|                           |                         | translated into 3       |
|                           |                         |                         |
|                           |                         | languages, the value of |
|                           |                         |                         |
|                           |                         | TotalTranslations would |
|                           |                         |                         |
|                           |                         | be 15.                  |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Integer                 | Number of free          |
|                           |                         |                         |
|    TranslationCredit      |                         | translations available  |
|                           |                         |                         |
|                           |                         | at the selected service |
|                           |                         |                         |
|                           |                         | level.                  |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | Currency that the price |
|                           |                         |                         |
|    Currency               |                         | is in. See glossary     |
|                           |                         |                         |
|                           |                         | for list of valid       |
|                           |                         |                         |
|                           |                         | currencies.             |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Decimal                 | Total price that needs  |
|                           |                         |                         |
|    TotalCost              |                         | to be paid. Exclude     |
|                           |                         |                         |
|                           |                         | translation credit.     |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Decimal                 | If a merchant has a     |
|                           |                         |                         |
|    PrepaidCredit          |                         | positive credit balance |
|                           |                         |                         |
|                           |                         | with onDemand, it will  |
|                           |                         |                         |
|                           |                         | be reported here.       |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Decimal                 | TotalCost -             |
|                           |                         | PrepaidCredit           |
|    AmountDue              |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | Method to track file    |
|                           |                         |                         |
|                           |                         | acceptance.             |
|                           |                         |                         |
|TranslationAcceptanceMethod|                         |                         |
|                           |                         |                         |
|                           |                         |                         |
|                           |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    |                         |                         |
|                           | Container               | Container of products   |
|    Projects               |                         |                         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Products            |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Container               | Container of SKU        |
|                           |                         |                         |
|    Projects               |                         | elements                |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Products            |                         |                         |
|                           |                         |                         |
|      .Product             |                         |                         |
|                           |                         |                         |
|      .SKUs                |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Container               | Container of a SKU      |
|                           |                         |                         |
|    Projects               |                         |                         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Products            |                         |                         |
|                           |                         |                         |
|      .Product             |                         |                         |
|                           |                         |                         |
|      .SKUs                |                         |                         |
|                           |                         |                         |
|      .SKU                 |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | Item SKU                |
|                           |                         |                         |
|    Projects               |                         |                         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Products            |                         |                         |
|                           |                         |                         |
|      .Product             |                         |                         |
|                           |                         |                         |
|      .SKUs                |                         |                         |
|                           |                         |                         |
|      .SKU                 |                         |                         |
|                           |                         |                         |
|      .SKUNumber           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Integer                 | onDemand internal ID    |
|                           |                         |                         |
|    Projects               |                         | for the listing         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Products            |                         |                         |
|                           |                         |                         |
|      .Product             |                         |                         |
|                           |                         |                         |
|      .AssetID             |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | String representing     |
|                           |                         |                         |
|    Projects               |                         | date/time (ISO 8601     |
|                           |                         |                         |
|      .Project             |                         | format) that the        |
|                           |                         |                         |
|      .Products            |                         | translation of the item |
|                           |                         |                         |
|      .Product             |                         | is scheduled to be      |
|                           |                         |                         |
|      .DueDate             |                         | completed in UTC        |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Integer                 | Asset ID of the file.   |
|                           |                         |                         |
|    Projects               |                         |                         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Files               |                         |                         |
|                           |                         |                         |
|      .File                |                         |                         |
|                           |                         |                         |
|      .AssetID             |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | Original name of the    |
|                           |                         |                         |
|    Projects               |                         | file.                   |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .Files               |                         |                         |
|                           |                         |                         |
|      .File                |                         |                         |
|                           |                         |                         |
|      .FileName            |                         |                         |
+---------------------------+-------------------------+-------------------------+
| Projects                  | Integer                 | ProjectID of included   |
|                           |                         |                         |
| .Project                  |                         | project                 |
|                           |                         |                         |
| .ProjectID                |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| Projects                  | String                  | The name of the project |
|                           |                         |                         |
| .Project                  |                         |                         |
|                           |                         |                         |
| .ProjectName              |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| Projects                  | Integer                 | The ID of the service   |
|                           |                         |                         |
| .Project                  |                         | used.                   |
|                           |                         |                         |
| .ServiceID                |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| Projects                  | String                  | The language code of    |
|                           |                         |                         |
| .Project                  |                         | source language.        |
|                           |                         |                         |
| .SourceLanguage           |                         |                         |
|                           |                         |                         |
| .LanguageCode             |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| Projects                  | String                  | The language code of    |
|                           |                         |                         |
| .Project                  |                         | a target language.      |
|                           |                         |                         |
| .TargetLanguages          |                         |                         |
|                           |                         |                         |
| .TargetLanguage           |                         |                         |
|                           |                         |                         |
| .LanguageCode             |                         |                         |
|                           |                         |                         |
|                           |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Container               | Container for a         |
|                           |                         |                         |
|    Projects               |                         | reference file. A       |
|                           |                         |                         |
|      .Project             |                         | reference file is used  |
|                           |                         |                         |
|      .ReferenceFiles      |                         | to inform the work that |
|                           |                         |                         |
|      .ReferenceFile       |                         | is being done. There is |
|                           |                         |                         |
|                           |                         | no charge for reference |
|                           |                         |                         |
|                           |                         | files.                  |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Integer                 | Asset ID of the         |
|                           |                         |                         |
|    Projects               |                         | reference file.         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .ReferenceFiles      |                         |                         |
|                           |                         |                         |
|      .ReferenceFile       |                         |                         |
|                           |                         |                         |
|      .AssetID             |                         |                         |
|                           |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | Original name of        |
|                           |                         |                         |
|    Projects               |                         | the file.               |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .ReferenceFiles      |                         |                         |
|                           |                         |                         |
|      .ReferenceFile       |                         |                         |
|                           |                         |                         |
|      .FileName            |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | String                  | URL where the file      |
|                           |                         |                         |
|    Projects               |                         | can be downloaded.      |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .ReferenceFiles      |                         |                         |
|                           |                         |                         |
|      .ReferenceFile       |                         |                         |
|                           |                         |                         |
|      .URL                 |                         |                         |
+---------------------------+-------------------------+-------------------------+
| .. container:: notrans    | Container               | Empty element.          |
|                           |                         |                         |
|    Projects               |                         |                         |
|                           |                         |                         |
|      .Project             |                         |                         |
|                           |                         |                         |
|      .ReferenceFiles      |                         |                         |
|                           |                         |                         |
|      .ReferenceFile       |                         |                         |
|                           |                         |                         |
|      .TargetLanguages     |                         |                         |
+---------------------------+-------------------------+-------------------------+

Product-Based Quote Response Example
====================================

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Pending</Status>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://</RejectURL>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>1</TranslationCredit>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
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
        <Errors></Errors>
    </Quote>

If the price is not yet ready, the response will look like:

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Calculating</Status>
        <TotalTranslations>2</TotalTranslations>
        <TranslationCredit>1</TranslationCredit>
        <TotalCost/>
        <PrepaidCredit/>5.00</PrepaidCredit>
        <AmountDue/>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
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
        <Errors></Errors>
    </Quote>

File-Based Quote Response Example
====================================

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Pending</Status>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://</RejectURL>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
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
                    <Files>
                            <File>
                                <AssetID>999</AssetID>
                                <FileName>example.txt</FileName>
                            </File>
                    </Files>
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
        <Errors></Errors>
    </Quote>

If the price is not yet ready, the response will look like:

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Calculating</Status>
        <TotalCost/>
        <PrepaidCredit/>5.00</PrepaidCredit>
        <AmountDue/>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
        <Projects>
            <Project>
                <Files>
                    <File>
                        <AssetID>999</AssetID>
                        <FileName>example.txt</FileName>
                    </File>
                </Files>
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
        <Errors></Errors>
    </Quote>

If one of or more files submitted are not compatible with the selected service, the response will look like

::

    <Quote>
        <Error>
            <ReasonCode>202</ReasonCode>
            <SimpleMessage>The file example.txt, is not supported by the Voiceover Translation Service</SimpleMessage>
            <DetailedMessage>The Video Translation Service only supports the following file types: .mov, .mp4, .flv, and .wmv</DetailedMessage>
        </Error>
    </Quote>

Project Based Quote Response Example
====================================

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Pending</Status>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://</RejectURL>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
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
                <ReferenceFiles/>
                </Project>
        </Projects>

        <Errors></Errors>
    </Quote>

If the price is not yet ready, the response will look like:

::

    <Quote>
        <QuoteID>132</QuoteID>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>Calculating</Status>
        <TotalCost/>
        <PrepaidCredit/>5.00</PrepaidCredit>
        <AmountDue/>
        <Currency>EUR</Currency>
        <TranslationAcceptanceMethod>implicit</TranslationAcceptanceMethod>
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
                    <ReferenceFiles/>
                </Project>
        </Projects>

        <Errors></Errors>
    </Quote>

If one of or more of the projects is already included in another quote, the response will look like this:
::

    <Quote>
        <Error>
            <ReasonCode>207</ReasonCode>
            <SimpleMessage>The Project(s) with IDs 1223, 2222 are already in use.</SimpleMessage>
            <DetailedMessage>
                Projects with the following IDs are already associated with another quote.
            </DetailedMessage>
        </Error>
    </Quote>



Errors
======
If generate quote encountered an error, the response will contain an Error element consisting of
a ReasonCode, SimpleMessage, and DetailedMessage elements. See :doc:`error_handling` for more
information. Here are some common cases.

+-------------------------+-------------------------+-------------------------+
| ReasonCode              | SimpleMessage           | DetailedMessage         |
+=========================+=========================+=========================+
| 200                     | Miscellaneous error     | A miscellaneous or      |
|                         |                         |                         |
|                         |                         | unexpected error        |
|                         |                         |                         |
|                         |                         | has occured.            |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 201                     | There was a problem     | Request body could not  |
|                         |                         |                         |
|                         | with the source content.| parsed. Please verify   |
|                         |                         |                         |
|                         |                         | that the XML is well-   |
|                         |                         |                         |
|                         |                         | formd and the encoding  |
|                         |                         |                         |
|                         |                         | is correct.             |
+-------------------------+-------------------------+-------------------------+
| 202                     | This service is not     | The selected service    |
|                         |                         |                         |
|                         | compatable with the     | does not support the    |
|                         |                         |                         |
|                         | submitted source        | submitted source        |
|                         |                         |                         |
|                         | content.                | content.                |
|                         |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 203                     | Asset does not exist.   | A file with this asset  |
|                         |                         |                         |
|                         |                         | ID does not exist in    |
|                         |                         |                         |
|                         |                         | the system.             |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 204                     | Asset is already in use.| One or more of the      |
|                         |                         |                         |
|                         |                         | referenced assets is    |
|                         |                         |                         |
|                         |                         | being used in another   |
|                         |                         |                         |
|                         |                         | project.                |
+-------------------------+-------------------------+-------------------------+
| 205                     | Incompatible Source     | File with id {id} is in |
|                         |                         |                         |
|                         | Language.               | the wrong language for  |
|                         |                         |                         |
|                         |                         | this project            |
+-------------------------+-------------------------+-------------------------+
| 206                     | Project does not exist. | A project with this     |
|                         |                         |                         |
|                         |                         | ID does not exist in    |
|                         |                         |                         |
|                         |                         | the system.             |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 207                     | Project is already in   | One or more of the      |
|                         |                         |                         |
|                         | use.                    | referenced projects is  |
|                         |                         |                         |
|                         |                         | being used in another   |
|                         |                         |                         |
|                         |                         | quote.                  |
+-------------------------+-------------------------+-------------------------+
