=========
Get Quote
=========

=============  ======================
**Resource:**  /api/quote/<<quote id>
**Method:**    GET
=============  ======================

Returns information about the merchant’s account

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

The response body contains information about the newly created merchant. 

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comment                 |
+=========================+=========================+=========================+
| QuoteID                 | Integer                 | onDemand ID for this    |
|                         |                         |                         |
|                         |                         | quote.                  |
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
| Projects                | Container               | A list of projects that |
|                         |                         |                         |
|                         |                         | have been generated by  |
|                         |                         |                         |
|                         |                         | this transaction.       |
+-------------------------+-------------------------+-------------------------+
| Projects                | Integer                 | onDemand Project ID for |
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
+-------------------------+-------------------------+-------------------------+
| Projects                | String                  | String representing the |
|                         |                         |                         |
| .Project                |                         | date/time (ISO 8601)    |
|                         |                         |                         |
| .ProjectDueDate         |                         | that the project will   |
|                         |                         |                         |
|                         |                         | be completed by.        |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | Container               | List of products        |
|                         |                         |                         |
| .Project                |                         | included in the         |
|                         |                         |                         |
| .Products               |                         | product.                |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | Container               | List of SKUs under      |
|                         |                         |                         |
| .Project                |                         | product                 |
|                         |                         |                         |
| .Products               |                         |                         |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | Container               | Contains a SKU          |
|                         |                         |                         |
| .Project                |                         |                         |
|                         |                         |                         |
| .Products               |                         |                         |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | String                  | Client supplied SKU     |
|                         |                         |                         |
| .Project                |                         | Number                  |
|                         |                         |                         |
| .Products               |                         |                         |
|                         |                         |                         |
| .Product                |                         |                         |
|                         |                         |                         |
| .SKUs                   |                         |                         |
|                         |                         |                         |
| .SKU                    |                         |                         |
|                         |                         |                         |
| .SKUNumber              |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Projects                | Integer                 | Internal onDemand ID    |
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

::

   <Quote>
        <QuoteID>132</QuoteID>
        <Status>Authorized</Status>
        <TotalCost>10.00</TotalCost>
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