==============
Create Account
==============

=============  ===================
**Resource:**  /api/account/create
**Method:**    POST
=============  ===================

This interface creates a new Account.  Access is restricted to an API account with create merchant privileges.  


Request Body
============

============  ======  ========
Parameter     Type    Comments
============  ======  ========
MerchantID    String  Merchant system account id
EmailAddress  String  Email address of the primary user
FirstName     String  First name of the primary user (optional)
LastName      String  Last name of the primary user (optional)
CompanyName   String  Merchant Company
Country       String  Country that the merchant is headquartered in.  `ISO 3166-1 2  character country code <http://en.wikipedia.org/wiki/ISO_3166-1>`_.
VATID         String  Tax ID for VAT accounting.  Required for Irish merchants only
============  ======  ========


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

===============   ======   ========
Property          Type     Comments
===============   ======   ========
MerchantID        String   Merchant system account id
EmailAddress      String   Email address of the primary user
FirstName         String   First name of the primary user (optional)
LastName          String   Last name of the primary user (optional)
CompanyName       String   Merchant Company
Country           String   Country that the merchant is headquartered in.  ISO 3166-1 2 character country code.    
AccessKeyID       String   String representing the 20 character access key id
SecretAccessKey   String   String representing the 40 character secret key.
===============   ======   ========
  

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
+-------------------------+-------------------------+-------------------------+
| 400                     | Miscellaneous error     | A miscellaneous or      |
|                         |                         |                         |
|                         |                         | unexpected error        |
|                         |                         |                         |
|                         |                         | has occured.            |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| 401                     | There was a problem     | Request body could not  |
|                         |                         |                         |
|                         | data in the request body| parsed. Please verify   |
|                         |                         |                         |
|                         |                         | that the XML is well-   |
|                         |                         |                         |
|                         |                         | formd and the encoding  |
|                         |                         |                         |
|                         |                         | is correct.             |
+-------------------------+-------------------------+-------------------------+
| 403                     | An account already      | A user account with     |
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
| 404                     | Merchant ID already in  | A user  account with    |
|                         |                         |                         |
|                         | use.                    | this merchant id        |
|                         |                         |                         |
|                         |                         | already exists.         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
