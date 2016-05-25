==========================
Request Quote Cancellation
==========================

+---------------+-------------------------------------------------+
| **Resource:** | .. container:: notrans                          |
|               |                                                 |
|               |    /api/quote/<<quote id>>/request-cancellation |
+---------------+-------------------------------------------------+
| **Method:**   | .. container:: notrans                          |
|               |                                                 |
|               |    POST                                         |
+---------------+-------------------------------------------------+

Creates a ZenDesk ticket for the quote cancellation request.

Arguments
=========

- **Quote ID:** The onDemand Quote ID.  You will receive this ID from :doc:`generate_quote` 


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


::

    <QuoteCancellationRequest>
        <Status>Success</Status>
    </QuoteCancellationRequest>
