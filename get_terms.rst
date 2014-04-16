========================
Get Terms and Conditions
========================

=============  ======================
**Resource:**  /api/terms
**Method:**    GET
=============  ======================

This interface retrieves the terms and conditions.

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

Response Body
=============

Returns an XHTML document containing the current terms and conditions


  

Response Example
================

::

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" 
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
        <head>
            <title>onDemand Terms and Conditions</title>
        </head>
        <body>
            <h2 class="bold">TERMS AND CONDITIONS</h2>
            <h3 class="bold">1.Introduction.</h3>
            <p>Your use of Lionbridge’s onDemand Services available on
            [www.liondemand.com] (the “Service”) is subject to these terms and
            conditions. In order to use the Service, you must open an account for
            the Service at [https://www.liondemand.com/accounts/register/] and
            accept these terms and conditions.  All subsequent orders you place for
            the Service are governed by our terms and conditions as then in effect.
            Through your use of the Service, you may select the particular type of
            onDemand Services as such are described in the Service.  Exhibit A sets
            out special provisions applicable to particular types of Services
            offered through the Service.  </p>
            ...
        </body>
    </html>