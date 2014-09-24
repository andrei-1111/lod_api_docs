==============
Reject Quote
==============

+---------------+-----------------------------------+
| **Resource:** | .. container:: notrans            |
|               |                                   |
|               |    /api/quote/<<quote id>>/reject |
+---------------+-----------------------------------+
| **Method:**   | .. container:: notrans            |
|               |                                   |
|               |    POST                           |
+---------------+-----------------------------------+

This interface rejects a quote that has already been created.  This deletes the quote.



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
| Conflict                | 409                     | This quote cannot be    |
|                         |                         |                         |
|                         |                         | rejected at this time.  |
|                         |                         |                         |
|                         |                         |  This is probably       |
|                         |                         |                         |
|                         |                         | because the projects    |
|                         |                         |                         |
|                         |                         | have already been       |
|                         |                         |                         |
|                         |                         | started.                |
+-------------------------+-------------------------+-------------------------+

Response Body
=============


::

    <RejectQuote>
        <Status>Success</Status>
        <Error>Error Message</Error>
    </RejectQuote>

