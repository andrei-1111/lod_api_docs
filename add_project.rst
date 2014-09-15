=============
Add Project
=============

=============  ============================
**Resource:**  /api/projects/add
**Method:**    POST
=============  ============================

Adds a new project to onDemand.  Should be used in conjunction with :doc:`generate_quote` to
make a purchase.

Depending on the service, either files or products can be submitted to be translated. Files can be uploaded prior to creating the project.
(see :doc:`add_file`)



Request Body
============

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| ProjectName             | String                  | Optional. String        |
|                         |                         |                         |
|                         |                         | representing the name   |
|                         |                         |                         |
|                         |                         | of the project.         |
|                         |                         |                         |
|                         |                         | Maximum 75 characters.  |
|                         |                         |                         |
|                         |                         | If this element is not  |
|                         |                         |                         |
|                         |                         | included, a name will   |
|                         |                         |                         |
|                         |                         | be generated.           |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | Container               | Contains information    |
|                         |                         |                         |
|                         |                         | specifying the          |
|                         |                         |                         |
|                         |                         | translation project.    |
+-------------------------+-------------------------+-------------------------+
| TranslationOptions      | String                  | Optional. String        |
|                         |                         |                         |
| .ProjectName            |                         | representing the name   |
|                         |                         |                         |
|                         |                         | of the project.  If     |
|                         |                         |                         |
|                         |                         | this element is not     |
|                         |                         |                         |
|                         |                         | included, a name will   |
|                         |                         |                         |
|                         |                         | be generated.           |
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
|                         |                         |                         |
|                         |                         | Elements. Products      |
|                         |                         |                         |
|                         |                         | are only allowed as     |
|                         |                         |                         |
|                         |                         | input if the service    |
|                         |                         |                         |
|                         |                         | supports products.      |
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
| .ItemSepecific          |                         |                         |
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
| .ItemSpecific           |                         |                         |
|                         |                         |                         |
| .Name                   |                         |                         |
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
| .ItemSpecific           |                         |                         |
|                         |                         |                         |
| .Value                  |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Files                   | Container               | A collection of file    |
|                         |                         |                         |
|                         |                         | elements. The files     |
|                         |                         |                         |
|                         |                         | referenced need to      |
|                         |                         |                         |
|                         |                         | supported by the        |
|                         |                         |                         |
|                         |                         | selected service.       |
|                         |                         |                         |
|                         |                         | See :doc:`list_services`|
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Files                   | Container               | A file is described     |
|                         |                         |                         |
| .File                   |                         | with a AssetID of a     |
|                         |                         |                         |
|                         |                         | previously uploaded file|
|                         |                         |                         |
|                         |                         | (see :doc:`add_file`)   |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Files                   | Integer                 | AssetID of previously   |
|                         |                         |                         |
| .File                   |                         | uploaded file. Note:    |
|                         |                         |                         |
| .AssetID                |                         | the file type needs to  |
|                         |                         |                         |
|                         |                         | be consistent with the  |
|                         |                         |                         |
|                         |                         | valid file types for    |
|                         |                         |                         |
|                         |                         | the service. Also,      |
|                         |                         |                         |
|                         |                         | a file cannot be        |
|                         |                         |                         |
|                         |                         | associated with more    |
|                         |                         |                         |
|                         |                         | that one quote.         |
+-------------------------+-------------------------+-------------------------+



Product Request Example
=======================

::

    <AddProject>
        <ProjectName>Name of the project</ProjectName>
        <TranslationOptions>
            <Currency>EUR</Currency>
            <NotificationURL>
                    `https://www.example.com/
            </NotificationURL>
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

    </AddProject>


File Request Example
====================

::

    <AddProject>
        <ProjectName>Name of the project</ProjectName>
        <TranslationOptions>
            <NotificationURL>
                    `https://www.example.com/
            </NotificationURL>
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
    </AddProject>

Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+-------------------------+-------------------------+-------------------------+
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

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| ProjectID               | Integer                 | onDemand ID of the      |
|                         |                         |                         |
|                         |                         | Project.                |
+-------------------------+-------------------------+-------------------------+
| ProjectName             | String                  | Either the submitted or |
|                         |                         |                         |
|                         |                         | or generated project    |
|                         |                         |                         |
|                         |                         | name.                   |
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
| Status                  | String                  | The status of the       |
|                         |                         |                         |
|                         |                         | project.                |
|                         |                         |                         |
|                         |                         | source content has been |
|                         |                         |                         |
|                         |                         | analyzed and the        |
|                         |                         |                         |
|                         |                         | project(s) has/have     |
|                         |                         |                         |
|                         |                         | been priced.            |
|                         |                         |                         |
|                         |                         | "Analyzing" means that  |
|                         |                         |                         |
|                         |                         | the price is still      |
|                         |                         |                         |
|                         |                         | being determined and    |
|                         |                         |                         |
|                         |                         | the client should       |
|                         |                         |                         |
|                         |                         | call :doc:`get_quote`   |
|                         |                         |                         |
|                         |                         | later to check on the   |
|                         |                         |                         |
|                         |                         | status.                 |
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
| TotalPrice              | Decimal                 | Total price that needs  |
|                         |                         |                         |
|                         |                         | to be paid. Exclude     |
|                         |                         |                         |
|                         |                         | translation credit.     |
+-------------------------+-------------------------+-------------------------+
| Currency                | String                  | Currency of the price   |
|                         |                         |                         |
|                         |                         | This is taken from the  |
|                         |                         |                         |
|                         |                         | default currency of the |
|                         |                         |                         |
|                         |                         | account profile         |
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
| Products                | String                  | String representing     |
|                         |                         |                         |
| .Product                |                         | date/time (ISO 8601     |
|                         |                         |                         |
| .DueDate                |                         | format) that the        |
|                         |                         |                         |
|                         |                         | translation of the item |
|                         |                         |                         |
|                         |                         | is scheduled to be      |
|                         |                         |                         |
|                         |                         | completed in UTC        |
+-------------------------+-------------------------+-------------------------+
| Files                   | Integer                 | Asset ID of the file.   |
|                         |                         |                         |
| .File                   |                         |                         |
|                         |                         |                         |
| .AssetID                |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Files                   | String                  | Original name of the    |
|                         |                         |                         |
| .File                   |                         | file.                   |
|                         |                         |                         |
| .FileName               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Files                   | String                  | String representing     |
|                         |                         |                         |
| .File                   |                         | date/time (ISO 8601     |
|                         |                         |                         |
| .DueDate                |                         | format) that the        |
|                         |                         |                         |
|                         |                         | translation of the item |
|                         |                         |                         |
|                         |                         | is scheduled to be      |
|                         |                         |                         |
|                         |                         | completed in UTC        |
+-------------------------+-------------------------+-------------------------+

Product-Based Project Response Example
=======================================

::

    <Project>
        <ProjectID>132</ProjectID>
        <ProjectName>Name of the project</ProjectName>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>New</Status>
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
        <TotalCost>10.00</TotalCost>
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
    </Project>

If the price is not yet ready, the response will look like:

::

    <Project>
        <ProjectID>132</ProjectID>
        <ProjectName>Name of the project</ProjectName>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>New</Status>
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
        <TotalCost/>
        <Currency>EUR</Currency>

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

File-Based Project Response Example
====================================

::

    <Project>
        <ProjectID>132</ProjectID>
        <ProjectName>Name of the project</ProjectName>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>New</Status>
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
        <TotalCost>10.00</TotalCost>
        <Currency>EUR</Currency>

        <Files>
            <File>
                <AssetID>999</AssetID>
                <FileName>example.txt</FileName>
                <DueDate>2014-02-11T10:22:46Z</DueDate> 
            </File>
        </Files>
    </Project>

If the price is not yet ready, the response will look like:

::

    <Project>
        <ProjectID>132</ProjectID>
        <ProjectName>Name of the project</ProjectName>
        <CreationDate>2014-01-25T10:32:02Z</CreationDate>
        <Status>New</Status>
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
        <TotalCost/>
        <AmountDue/>
        <Currency>EUR</Currency>

        <Files>
                <File>
                    <AssetID>999</AssetID>
                    <FileName>example.txt</FileName>
                </File>
        </Files>
    </Project>

If one of or more files submitted are not compatible with the selected service, the response will look like

::

    <Project>
        <Error>
            <ReasonCode>202</ReasonCode>
            <SimpleMessage>The file example.txt, is not supported by the Voiceover Translation Service</SimpleMessage>
            <DetailedMessage>The Video Translation Service only supports the following file types: .mov, .mp4, .flv, and .wmv</DetailedMessage>
        </Error>
    </Project>


Errors
======
If generate quote encountered an error, the response will contain an Error element consisting of
a ReasonCode, SimpleMessage, and DetailedMessage elements. See :doc:`error_handling` for more 
information. Here are some common cases.

+-------------------------+-------------------------+-------------------------+
| ReasonCode              | SimpleMessage           | DetailedMessage         |
+-------------------------+-------------------------+-------------------------+
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

