==============
Create Account
==============

+-----------------+------------------------+
| **Resource:**   | .. container:: notrans |
|                 |                        |
|                 |    /api/account/create |
+-----------------+------------------------+
| **Method:**     | .. container:: notrans |
|                 |                        |
|                 |    POST                |
+-----------------+------------------------+

This interface creates a new Account.  Access is restricted to an API account with create merchant privileges.  


Request Body
============

+-------------------------+-------------------+------------------------------------------------+
| Parameter               | Type              | Comments                                       |
+=========================+===================+================================================+
| .. container:: notrans  | String (optional) | Merchant system account id (optional)          |
|                         |                   |                                                |
|    MerchantID           |                   |                                                |
+-------------------------+-------------------+------------------------------------------------+
| .. container:: notrans  | String            | Email address of the primary user              |
|                         |                   |                                                |
|    EmailAddress         |                   |                                                |
+-------------------------+-------------------+------------------------------------------------+
| .. container:: notrans  | String            | First name of the primary user                 |
|                         |                   |                                                |
|    FirstName            |                   |                                                |
+-------------------------+-------------------+------------------------------------------------+
| .. container:: notrans  | String            | Last name of the primary user                  |
|                         |                   |                                                |
|    LastName             |                   |                                                |
+-------------------------+-------------------+------------------------------------------------+
| .. container:: notrans  | String            | Merchant Company                               |
|                         |                   |                                                |
|    CompanyName          |                   |                                                |
+-------------------------+-------------------+------------------------------------------------+
| .. container:: notrans  | String            | Country that the merchant is headquartered in. |
|                         |                   | `ISO 3166-1 2  character country code          |
|    Country              |                   | <http://en.wikipedia.org/wiki/ISO_3166-1>`_.   |
+-------------------------+-------------------+------------------------------------------------+
| .. container:: notrans  | String (optional) | Tax ID for VAT accounting.  Required for Irish |
|                         |                   | merchants only                                 |
|    VATID                |                   |                                                |
+-------------------------+-------------------+------------------------------------------------+


Request Example
===============

::

    <CreateAccount>
        <MerchantID>123233244</MerchantID>
        <EmailAddress>example@example.com</EmailAddress>
        <FirstName>Joe</FirstName>
        <LastName>Bloggs</LastName>
        <CompanyName>ACME Coyote Products, Ltd.</CompanyName>
        <Country>GB</Country>
        <VATID>12334455544</VATID>
    </CreateAccount> 


Return Codes
============

============  ====   ========
Status        Code   Comments
============  ====   ========
Created       201    The project was created
Bad Request   400    Potentially from an invalid country code or a missing VATID.
Unauthorized  401    The request did not pass authentication or the customer is not a member of an enterprie   site.
Conflict      409    A merchant with this ID or email address already exists.  
============  ====   ========

Response Body
=============

The response body contains information about the newly created merchant. 

+-------------------------+--------+------------------------------------------------+
| Property                | Type   | Comments                                       |
+=========================+========+================================================+
| .. container:: notrans  | String | Merchant system account id                     |
|                         |        |                                                |
|    MerchantID           |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | Email address of the primary user              |
|                         |        |                                                |
|    EmailAddress         |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | First name of the primary user (optional)      |
|                         |        |                                                |
|    FirstName            |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | Last name of the primary user (optional)       |
|                         |        |                                                |
|    LastName             |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | Merchant Company                               |
|                         |        |                                                |
|    CompanyName          |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | Country that the merchant is headquartered in. |
|                         |        | ISO 3166-1 2  character country code.          |
|    Country              |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | String representing the 20 character access    |
|                         |        | key id                                         |
|    AccessKeyID          |        |                                                |
+-------------------------+--------+------------------------------------------------+
| .. container:: notrans  | String | String representing the 40 character secret    |
|                         |        | key.                                           |
|    SecretAccessKey      |        |                                                |
+-------------------------+--------+------------------------------------------------+
  

Response Example
================

::

    <Account>
        <MerchantID>123233244</MerchantID>
        <Status>Created</Status>
        <EmailAddress>example@example.com</EmailAddress>
        <FirstName>Joe</FirstName>
        <LastName>Bloggs</LastName>
        <CompanyName>ACME Coyote Products, Ltd.</CompanyName>
        <Country>GB</Country>
        <AccessKeyID>qzwBzqCiMsuHoUrZEcLqgH</AccessKeyID>
        <SecretAccessKey>znkcyBjEWKQFIELAkotspHDoJbwHJyRPXChFYWDn</SecretAccessKey>
    </Account> 


Errors
======
If generate quote encountered an error, the response will contain an Error element consisting of
a ReasonCode, SimpleMessage, and DetailedMessage elements. See :doc:`error_handling` for more 
information. Here are some common cases.

+-------------------------+-------------------------+-------------------------+
| ReasonCode              | SimpleMessage           | DetailedMessage         |
+=========================+=========================+=========================+
| 400                     | Miscellaneous error     | A miscellaneous or      |
|                         |                         |                         |
|                         |                         | unexpected error        |
|                         |                         |                         |
|                         |                         | has occurred.           |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 401                     | There was a problem     | Request body could not  |
|                         |                         |                         |
|                         | data in the request body| be parsed. Please verify|
|                         |                         |                         |
|                         |                         | that the XML is well-   |
|                         |                         |                         |
|                         |                         | formed and the encoding |
|                         |                         |                         |
|                         |                         | is correct.             |
+-------------------------+-------------------------+-------------------------+
| 404                     | An account already      | A user account with     |
|                         |                         |                         |
|                         | exists.                 | this email already      |
|                         |                         |                         |
|                         |                         | exists. The user should |
|                         |                         |                         |
|                         |                         | log into onDemand and   |
|                         |                         |                         |
|                         |                         | copy his access keys.   |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
