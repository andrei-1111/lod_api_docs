=============
Add Project
=============

+-----------------+------------------------+
| **Resource:**   | .. container:: notrans |
|                 |                        |
|                 |    /api/projects/add   |
+-----------------+------------------------+
| **Method:**     | .. container:: notrans |
|                 |                        |
|                 |    POST                |
+-----------------+------------------------+

Adds a new project to onDemand.  Should be used in conjunction with :doc:`generate_quote` to
make a purchase.

Depending on the service, either files or products can be submitted to be translated. Files can be uploaded prior to creating the project.
(see :doc:`add_file`)



Request Body
============

+-------------------------+-------------------------+---------------------------------+
| Parameter               | Type                    | Comments                        |
+=========================+=========================+=================================+
| .. container:: notrans  | String (optional)       | String representing the         |
|                         |                         |                                 |
|    ProjectName          |                         | name of the project.            |
|                         |                         |                                 |
|                         |                         | Maximum 75 characters.          |
|                         |                         |                                 |
|                         |                         | If this element is not          |
|                         |                         |                                 |
|                         |                         | included, a name will           |
|                         |                         |                                 |
|                         |                         | be generated.                   |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains information            |
|                         |                         |                                 |
|    TranslationOptions   |                         | specifying the                  |
|                         |                         |                                 |
|                         |                         | translation project.            |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Integer                 | Numeric service code            |
|                         |                         |                                 |
|    TranslationOptions   |                         | for the translation             |
|                         |                         |                                 |
|      .ServiceID         |                         | service.  The service           |
|                         |                         |                                 |
|                         |                         | defines a set of                |
|                         |                         |                                 |
|                         |                         | options such as machine         |
|                         |                         |                                 |
|                         |                         | translation with post           |
|                         |                         |                                 |
|                         |                         | edit on the title and           |
|                         |                         |                                 |
|                         |                         | raw machine translation         |
|                         |                         |                                 |
|                         |                         | on the body.  This              |
|                         |                         |                                 |
|                         |                         | element is optional.            |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains 1 source               |
|                         |                         |                                 |
|    TranslationOptions   |                         | language                        |
|                         |                         |                                 |
|      .SourceLanguage    |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | See LanguageCode in             |
|                         |                         |                                 |
|    TranslationOptions   |                         | glossary                        |
|                         |                         |                                 |
|      .SourceLanguage    |                         |                                 |
|                         |                         |                                 |
|      .LanguageCode      |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains 1 or more              |
|                         |                         |                                 |
|    TranslationOptions   |                         | target languages                |
|                         |                         |                                 |
|      .TargetLanguages   |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | See LanguageCode in             |
|                         |                         |                                 |
|    TranslationOptions   |                         | glossary                        |
|                         |                         |                                 |
|      .TargetLanguages   |                         |                                 |
|                         |                         |                                 |
|      .TargetLanguage    |                         |                                 |
|                         |                         |                                 |
|      .LanguageCode      |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | List                    | List of Product                 |
|                         |                         |                                 |
|    Products             |                         | Elements. Products              |
|                         |                         |                                 |
|                         |                         | are only allowed as             |
|                         |                         |                                 |
|                         |                         | input if the service            |
|                         |                         |                                 |
|                         |                         | supports products.              |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | The title of the                |
|                         |                         |                                 |
|    Products             |                         | product                         |
|                         |                         |                                 |
|      .Product           |                         |                                 |
|                         |                         |                                 |
|      .Title             |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Integer                 | ID of the product’s             |
|                         |                         |                                 |
|    Products             |                         | primary category                |
|                         |                         |                                 |
|      .Product           |                         |                                 |
|                         |                         |                                 |
|      .PrimaryCategory   |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Integer                 | ID of the top level             |
|                         |                         |                                 |
|    Products             |                         | category that the               |
|                         |                         |                                 |
|      .Product           |                         | product sits in                 |
|                         |                         |                                 |
|      .TopLevelCategory  |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | Delimited string                |
|                         |                         |                                 |
|    Products             |                         | showing the path                |
|                         |                         |                                 |
|      .Product           |                         | through the category            |
|                         |                         |                                 |
|      .Category          |                         | hierarchy to the                |
|                         |                         |                                 |
|                         |                         | primary category.  This         |
|                         |                         |                                 |
|                         |                         | is mainly for                   |
|                         |                         |                                 |
|                         |                         | contextual information          |
|                         |                         |                                 |
|                         |                         | for the translators.            |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | The description of the          |
|                         |                         |                                 |
|    Products             |                         | item.  This element can         |
|                         |                         |                                 |
|      .Product           |                         | contain sub-elements.           |
|                         |                         |                                 |
|      .Description       |                         | HTML that is not well           |
|                         |                         |                                 |
|                         |                         | formed XML should be            |
|                         |                         |                                 |
|                         |                         | wrapped in CDATA tags.          |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains a SKU elements         |
|                         |                         |                                 |
|    Products             |                         |                                 |
|                         |                         |                                 |
|      .Product           |                         |                                 |
|                         |                         |                                 |
|      .SKUs              |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains a SKU Number           |
|                         |                         |                                 |
|    Products             |                         | and a list of                   |
|                         |                         |                                 |
|      .Product           |                         | ItemSpecifics that are          |
|                         |                         |                                 |
|      .SKUs              |                         | relevant to the SKU             |
|                         |                         |                                 |
|      .SKU               |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | SKU Number                      |
|                         |                         |                                 |
|    Products             |                         |                                 |
|                         |                         |                                 |
|      .Product           |                         |                                 |
|                         |                         |                                 |
|      .SKUs              |                         |                                 |
|                         |                         |                                 |
|      .SKU               |                         |                                 |
|                         |                         |                                 |
|      .SKUNumber         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains elements               |
|                         |                         |                                 |
|    Products             |                         | representing                    |
|                         |                         |                                 |
|      .Product           |                         | specifications.                 |
|                         |                         |                                 |
|      .SKUs              |                         |                                 |
|                         |                         |                                 |
|      .SKU               |                         |                                 |
|                         |                         |                                 |
|      .ItemSpecifics     |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Contains elements               |
|                         |                         |                                 |
|    Products             |                         | representing name-value         |
|                         |                         |                                 |
|      .Product           |                         | pairs                           |
|                         |                         |                                 |
|      .SKUs              |                         |                                 |
|                         |                         |                                 |
|      .SKU               |                         |                                 |
|                         |                         |                                 |
|      .ItemSpecifics     |                         |                                 |
|                         |                         |                                 |
|      .ItemSepecific     |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | The name of the name            |
|                         |                         |                                 |
|    Products             |                         | value pair                      |
|                         |                         |                                 |
|      .Product           |                         |                                 |
|                         |                         |                                 |
|      .SKUs              |                         |                                 |
|                         |                         |                                 |
|      .SKU               |                         |                                 |
|                         |                         |                                 |
|      .ItemSpecifics     |                         |                                 |
|                         |                         |                                 |
|      .ItemSpecific      |                         |                                 |
|                         |                         |                                 |
|      .Name              |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | String                  | The name of the name            |
|                         |                         |                                 |
|    Products             |                         | value pair                      |
|                         |                         |                                 |
|      .Product           |                         |                                 |
|                         |                         |                                 |
|      .SKUs              |                         |                                 |
|                         |                         |                                 |
|      .SKU               |                         |                                 |
|                         |                         |                                 |
|      .ItemSpecifics     |                         |                                 |
|                         |                         |                                 |
|      .ItemSpecific      |                         |                                 |
|                         |                         |                                 |
|      .Value             |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | A collection of file            |
|                         |                         |                                 |
|    Files                |                         | elements. The files             |
|                         |                         |                                 |
|                         |                         | referenced need to              |
|                         |                         |                                 |
|                         |                         | supported by the                |
|                         |                         |                                 |
|                         |                         | selected service.               |
|                         |                         |                                 |
|                         |                         | See :doc:`list_services`        |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | A file is described             |
|                         |                         |                                 |
|    Files                |                         | with a AssetID of a             |
|                         |                         |                                 |
|      .File              |                         | previously uploaded file        |
|                         |                         |                                 |
|                         |                         | (see :doc:`add_file`)           |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Integer                 | AssetID of previously           |
|                         |                         |                                 |
|    Files                |                         | uploaded file. Note:            |
|                         |                         |                                 |
|      .File              |                         | the file type needs to          |
|                         |                         |                                 |
|      .AssetID           |                         | be consistent with the          |
|                         |                         |                                 |
|                         |                         | valid file types for            |
|                         |                         |                                 |
|                         |                         | the service. Also,              |
|                         |                         |                                 |
|                         |                         | a file cannot be                |
|                         |                         |                                 |
|                         |                         | associated with more            |
|                         |                         |                                 |
|                         |                         | that one quote.                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Container               | Container for a                 |
|                         |                         |                                 |
|    ReferenceFiles       |                         | reference file. A               |
|                         |                         |                                 |
|      .ReferenceFile     |                         | reference file is used          |
|                         |                         |                                 |
|                         |                         | to inform the work that         |
|                         |                         |                                 |
|                         |                         | is being done. There is         |
|                         |                         |                                 |
|                         |                         | no charge for reference         |
|                         |                         |                                 |
|                         |                         | files.                          |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
| .. container:: notrans  | Integer                 | Asset ID of the                 |
|                         |                         |                                 |
|    ReferenceFiles       |                         | reference file.                 |
|                         |                         |                                 |
|      .ReferenceFile     |                         |                                 |
|                         |                         |                                 |
|      .AssetID           |                         |                                 |
|                         |                         |                                 |
+-------------------------+-------------------------+---------------------------------+
        


Product Request Example
=======================

::

    <AddProject>
        <ProjectName>Name of the project</ProjectName>
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

    </AddProject>


File Request Example
====================

::

    <AddProject>
        <ProjectName>Name of the project</ProjectName>
        <TranslationOptions>
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
    </AddProject>

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

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | Integer                 | onDemand ID of the      |
|                         |                         |                         |
|    ProjectID            |                         | Project.                |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Either the submitted or |
|                         |                         |                         |
|    ProjectName          |                         | or generated project    |
|                         |                         |                         |
|                         |                         | name.                   |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing the |
|                         |                         |                         |
|    CreationDate         |                         | date/time in the ISO    |
|                         |                         |                         |
|                         |                         | 8601 format. that the   |
|                         |                         |                         |
|                         |                         | project was created in  |
|                         |                         |                         |
|                         |                         | UTC.                    |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | The status of the       |
|                         |                         |                         |
|    Status               |                         | project.                |
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
|      .TargetLanguage    |                         |                         |
|                         |                         |                         |
|      .LanguageCode      |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | Total price that needs  |
|                         |                         |                         |
|    Price                |                         | to be paid. Exclude     |
|                         |                         |                         |
|                         |                         | translation credit.     |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Currency of the price   |
|                         |                         |                         |
|    Currency             |                         | This is taken from the  |
|                         |                         |                         |
|                         |                         | default currency of the |
|                         |                         |                         |
|                         |                         | account profile         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of products   |
|                         |                         |                         |
|    Products             |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of SKU        |
|                         |                         |                         |
|    Products             |                         | elements                |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKUs              |                         |                         | 
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container of a SKU      |
|                         |                         |                         |
|    Products             |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKUs              |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Item SKU                |
|                         |                         |                         |
|    Products             |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKUs              |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
|                         |                         |                         |
|      .SKUNumber         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | onDemand internal ID    |
|                         |                         |                         |
|    Products             |                         | for the listing         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .AssetID           |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    Products             |                         | date/time (ISO 8601     |
|                         |                         |                         |
|      .Product           |                         | format) that the        |
|                         |                         |                         |
|      .DueDate           |                         | translation of the item |
|                         |                         |                         |
|                         |                         | is scheduled to be      |
|                         |                         |                         |
|                         |                         | completed in UTC        |
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
| .. container:: notrans  | String                  | String representing     |
|                         |                         |                         |
|    Files                |                         | date/time (ISO 8601     |
|                         |                         |                         |
|      .File              |                         | format) that the        |
|                         |                         |                         |
|      .DueDate           |                         | translation of the item |
|                         |                         |                         |
|                         |                         | is scheduled to be      |
|                         |                         |                         |
|                         |                         | completed in UTC        |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Container for a         |
|                         |                         |                         |
|    ReferenceFiles       |                         | reference file. A       |
|                         |                         |                         |
|      .ReferenceFile     |                         | reference file is used  |
|                         |                         |                         |
|                         |                         | to inform the work that |
|                         |                         |                         |
|                         |                         | is being done. There is |
|                         |                         |                         |
|                         |                         | no charge for reference |
|                         |                         |                         |
|                         |                         | files.                  |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | Asset ID of the         |
|                         |                         |                         |
|    ReferenceFiles       |                         | reference file.         |
|                         |                         |                         |
|      .ReferenceFile     |                         |                         |
|                         |                         |                         |
|      .AssetID           |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Original name of        |
|                         |                         |                         |
|    ReferenceFiles       |                         | the file.               |
|                         |                         |                         |
|      .ReferenceFile     |                         |                         |
|                         |                         |                         |
|      .FileName          |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | URL where the file can  |
|                         |                         |                         |
|    ReferenceFiles       |                         | be downloaded.          |
|                         |                         |                         |
|      .ReferenceFile     |                         |                         |
|                         |                         |                         |
|      .URL               |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Empty element.          |
|                         |                         |                         |
|    ReferenceFiles       |                         |                         |
|                         |                         |                         |
|      .ReferenceFile     |                         |                         |
|                         |                         |                         |
|      .TargetLanguages   |                         |                         |
|                         |                         |                         |
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
        <Price>10.00</Price>
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
        <Price/>
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

