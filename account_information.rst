===================
Account Information
===================

+-----------------+------------------------+
| **Resource:**   | .. container:: notrans |
|                 |                        |
|                 |    /api/account/info   |
+-----------------+------------------------+
| **Method:**     | .. container:: notrans |
|                 |                        |
|                 |    GET                 |
+-----------------+------------------------+

Returns information about the merchant’s account

Return Codes
============

============  ====   ========
Status        Code   Comments
============  ====   ========
Successs      200    The account information was retrieved
Unauthorized  401    The request did not pass authentication or the customer is not a member of an enterprise   site.
============  ====   ========

Response Body
=============

The response body contains information the buyer account.

+--------------------------+-----------+----------------------------------------------+
| Property                 | Type      | Comments                                     |
+==========================+===========+==============================================+
| .. container:: notrans   | String    | Email address associated with the address    |
|                          |           |                                              |
|    Email                 |           |                                              |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | String    | Currency that the merchant is configured to  |
|                          |           |                                              |
|    Currency              |           | transact in. See glossary for list of valid  |
|                          |           |                                              |
|                          |           | currencies.                                  |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | Decimal   | Total money spent in the merchant's currency |
|                          |           |                                              |
|    TotalSpent            |           |                                              |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | Integer   | Number of translations granted to the        |
|                          |           | merchant.                                    |
|    TranslationCredit     |           |                                              |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | Integer   | Number of credit translations used.          |
|                          |           |                                              |
|    TranslationCreditUsed |           |                                              |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | Decimal   | Amount of pre-paid funds in the merchant’s   |
|                          |           |                                              |
|    PrepaidCredit         |           | account.                                     |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | Integer   | Number of Products that have been submitted  |
|                          |           |                                              |
|    ProductCount          |           | to the service.                              |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | Container | Contains languages that the merchant has     |
|                          |           |                                              |
|    TargetLanguages       |           | translated into.                             |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | String    | See LanguageCode in glossary                 |
|                          |           |                                              |
|    TargetLanguages       |           |                                              |
|                          |           |                                              |
|      .TargetLanguage     |           |                                              |
|                          |           |                                              |
|      .LanguageCode       |           |                                              |
+--------------------------+-----------+----------------------------------------------+
| .. container:: notrans   | String    | Number of products translated into this      |
|                          |           |                                              |
|    TargetLanguages       |           | language                                     |
|                          |           |                                              |
|      .TargetLanguage     |           |                                              |
|                          |           |                                              |
|      .Count              |           |                                              |
+--------------------------+-----------+----------------------------------------------+

  

Response Example
================

::

    <Account>
        <Email>example@example.com</Email>
        <Currency>GBP</Currency>
        <TotalSpent>10000.00</TotalSpent>
        <TranslationCredit>500</TranslationCredit>
        <TranslationCreditUsed>100</TranslationCreditUsed>
        <PrepaidCredit>1000.00</PrepaidCredit>
        <ProductCount>24</ProductCount>
        <TargetLanguages>
            <TargetLanguage>
                <LanguageCode>fr-fr</LanguageCode>
                <Count>1000</Count>
            </TargetLangauge>
            <TargetLanguage>
                <LanguageCode>it-it</LanguageCode>
                <Count>1000</Count>
            </TargetLangauge>
        </TargetLanguages>
    </Account>
