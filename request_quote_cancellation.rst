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

Submits a request to cancel a purchased quote. This API can only be use on quotes that in a started or partially completed state. The request will be reviewed by the Lionbridge team. Depending on how much work has been completed on the projects, Lionbridge may issue a partial or full refund.

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
