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
Country       String  Country that the merchant is headquartered in.  ISO 3166-1 2  character country code.
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
        <Country>uk</Country>
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
        <EmailAddress>example@example.com</EmailAddress>
        <FirstName>Joe</FirstName>
        <LastName>Bloggs</LastName>
        <CompanyName>ACME Coyote Products, Ltd.</CompanyName>
        <Country>uk</Country>
        <AccessKeyID>qzwBzqCiMsuHoUrZEcLqgH</AccessKeyID>
        <SecretAccessKey>znkcyBjEWKQFIELAkotspHDoJbwHJyRPXChFYWDn</SecretAccessKey>
    </Account> 
