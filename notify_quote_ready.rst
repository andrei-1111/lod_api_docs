========================
Quote Ready Notification
========================

If a quote was generated with an http-based notification subscription to the quote ready event, 
the API will post the following informattion to that URL when the quote has been priced and is ready for payment.



Request Body
=============

The response body contains information about the newly created merchant. 

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comment                 |
+=========================+=========================+=========================+
| .. container:: notrans  | Integer                 | onDemand ID for this    |
|                         |                         |                         |
|    QuoteID              |                         | quote.                  |
+-------------------------+-------------------------+-------------------------+
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
| .. container:: notrans  | String                  | See                     |
|                         |                         |                         |
|    AuthorizeURL         |                         | :doc:`authorize_quote`  |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | See                     |
|                         |                         |                         |
|     RejectURL           |                         | :doc:`reject_quote`     |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Currency that the price |
|                         |                         |                         |
|    Currency             |                         | is in. See glossary     |
|                         |                         |                         |
|                         |                         | for list of valid       |
|                         |                         |                         |
|                         |                         | currencies.             |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | Total amount that needs |
|                         |                         |                         |
|    TotalCost            |                         | to be paid. Exclude     |
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
| .. container:: notrans  | Decimal                 | TotalCost -             |
|                         |                         |                         |
|    AmountDue            |                         | Prepaid Credit          |
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
| .. container:: notrans  | Container               | List of SKUs under      |
|                         |                         |                         |
|    Projects             |                         | product                 |
|                         |                         |                         |
|      .Project           |                         |                         |
|                         |                         |                         |
|      .Products          |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKUs              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Container               | Contains a SKU          |
|                         |                         |                         |
|    Projects             |                         |                         |
|                         |                         |                         |
|      .Project           |                         |                         |
|                         |                         |                         |
|      .Products          |                         |                         |
|                         |                         |                         |
|      .Product           |                         |                         |
|                         |                         |                         |
|      .SKUs              |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
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
|      .SKUs              |                         |                         |
|                         |                         |                         |
|      .SKU               |                         |                         |
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
| .. container:: notrans  | String                  | See :doc:`list_files`   |
|                         |                         |                         |
|    Files                |                         | for a list of file      |
|                         |                         |                         |
|      .File              |                         | statuses.               |
|                         |                         |                         |
|      .Status            |                         |                         |
+-------------------------+-------------------------+-------------------------+

  

Product-Based Quote Request Example
====================================

::

   <Quote>
        <QuoteID>132</QuoteID>
        <Status>Pending</Status>
        <TotalCost>10.00</TotalCost>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://…</RejectURL>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
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
    </Quote>


File-Based Quote Request Example
====================================

::

   <Quote>
        <QuoteID>132</QuoteID>
        <Status>Pending</Status>
        <TotalCost>10.00</TotalCost>
        <AuthorizeURL>https://…</AuthorizeURL>
        <RejectURL>https://…</RejectURL>
        <TotalCost>10.00</TotalCost>
        <PrepaidCredit>5.00</PrepaidCredit>
        <AmountDue>5.00</AmountDue>
        <Currency>EUR</Currency>
        <Projects>
            <Project>
                <ProjectID>123</ProjectID>
                <ProjectName>Name of project</ProjectName>
                <ProjectURL>https://</ProjectURL>
                <ProjectDueDate>2014-02-11T10:22:46Z</ProjectDueDate>
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



