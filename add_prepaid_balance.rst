===================
Add Prepaid Balance
===================

=============  ===============================
**Resource:**  /api/account/credit-balance/add
**Method:**    POST
=============  ===============================

This interface adds money to a prepaid balance that can be used to pay for 
onDemand projects.  The general flow is like this.

.. image:: /_static/img/top_up_flow.png
   :alt: alternate text
   :align: center


Request Body
============

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| Amount                  | Decimal (2 digits)      | Amount of of money to   |
|                         |                         |                         |
|                         |                         | add to the balance      |
|                         |                         |                         |
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

Request Example
===============

::

    <AddCreditBalance>
        <Amount>100.00</Amount>
        <Currency>USD</Currency>
    </AddCreditBalance>

Return Codes
============


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| OK                      | 200                     | The request was accepted|
|                         |                         |                         |
|                         |                         | the response will       |
|                         |                         |                         |
|                         |                         | contain a link to a     |
|                         |                         |                         |
|                         |                         | payment page.           |
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

The response body contains information about the credit balance request 
including a payment URL.  The user must follow this URL to a payment page.

+-------------------------+-------------------------+-------------------------+
| Parameter               | Type                    | Comments                |
+-------------------------+-------------------------+-------------------------+
| Amount                  | Decimal (2 digits)      | Amount of of money to   |
|                         |                         |                         |
|                         |                         | add to the balance      |
|                         |                         |                         |
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
| PaymentURL              | String                  | URL of payment page     |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+






Response Example
================

::

    <AddCreditBalance>
        <Amount>100.00</Amount>
        <Currency>USD</Currency>
        <PaymentURL>https://...</PaymentURL>
    </AddCreditBalance>
