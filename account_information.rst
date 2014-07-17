===================
Account Information
===================

=============  ===================
**Resource:**  /api/account/info
**Method:**    GET
=============  ===================

Returns information about the merchant’s account

Return Codes
============

============  ====   ========
Status        Code   Comments
============  ====   ========
Successs      200    The project was created
Bad Request   400    Potentially from an invalid country code or a missing VATID.
Unauthorized  401    The request did not pass authentication or the customer is not a member of an enterprise   site.
============  ====   ========

Response Body
=============

The response body contains information the buyer account.

+----------------------+----------+----------------------------------------------+
| Property             |Type      |Comments                                      |
+======================+==========+==============================================+
| Email                | String   | Email address associated with the address    |
+----------------------+----------+----------------------------------------------+
| Currency             | String   | Currency that the merchant is configured to  |
|                      |          |                                              |
|                      |          | transact in. See glossary for list of valid  |
|                      |          |                                              |
|                      |          | currencies.                                  |
+----------------------+----------+----------------------------------------------+
| TotalSpent           | Decimal  | Total money spent in the merchant's currency |
|                      |          |                                              |
+----------------------+----------+----------------------------------------------+
| TranslationCredit    | Integer  | Number of translations granted to the        |
|                      |          | merchant.                                    |
+----------------------+----------+----------------------------------------------+
| TranslationCreditUsed| Integer  | Number of credit translations used.          |
+----------------------+----------+----------------------------------------------+
| PrepaidCredit        | Decimal  | Amount of pre-paid funds in the merchant’s   |
|                      |          |                                              |
|                      |          | account.                                     |
+----------------------+----------+----------------------------------------------+
| ProductCount         | Integer  | Number of Products that have been submitted  |
|                      |          |                                              |
|                      |          | to the service.                              |
+----------------------+----------+----------------------------------------------+
|TargetLanguages       | Container| Contains languages that the merchant has     |
|                      |          |                                              |
|                      |          | translated into.                             |
+----------------------+----------+----------------------------------------------+
|TargetLanguages       | String   | See LanguageCode in glossary                 |
|                      |          |                                              |
| .TargetLanguage      |          |                                              |
|                      |          |                                              |
| .LanguageCode        |          |                                              |
+----------------------+----------+----------------------------------------------+
| TargetLanguages      | String   | Number of products translated into this      |
|                      |          |                                              |
|  .TargetLanguage     |          | language                                     |
|                      |          |                                              |
|  .Count              |          |                                              |
+----------------------+----------+----------------------------------------------+

  

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
