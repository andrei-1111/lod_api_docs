=============
Get Estimate
=============

+---------------+----------------------------------------------------------------------------------------------------+
| **Resource:** | .. container:: notrans                                                                             |
|               |                                                                                                    |
|               |    /api/estimate?service_id=10&unit_count=10&source_lang=en-gb&target_langs=it-it,de-de            |
+---------------+----------------------------------------------------------------------------------------------------+
| **Method:**   | .. container:: notrans                                                                             |
|               |                                                                                                    |
|               |    GET                                                                                             |
+---------------+----------------------------------------------------------------------------------------------------+

The Get Estimate API is used to get a rough estimate for a project based on the parameters listed below.  It is useful 
for client applications that are capable of counting words and that want to give the end customer a rough estimate of how 
much a project will cost.  Please note, the estimate will not be the same as the actual price if the onDemand word counting 
algorithm produces a different result than the client application.  





Querystring Arguments
=====================

- **service_id:** (required) The ID of the service. 
- **currency:** (optional) The three letter currency code.  If it is not passed, the quote will be generated in currency set in the user's profile.
- **unit_count:** (required) The number of units (words, pages, minutes, etc.) that will be processed.
- **source_lang:** (required) The langauge code of the source language
- **target_langs:** (required) A comma delimited list of target language codes




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

The response body details about a single service.
 

+-------------------------+-------------------------+-------------------------+
| Property                | Type                    | Comments                |
+=========================+=========================+=========================+
| .. container:: notrans  | Container               | Contains information    |
|                         |                         |                         |
|    Service              |                         | about the service being |
|                         |                         |                         |
|                         |                         | quoted.                 |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Integer                 | ID of the service.      |
|                         |                         |                         |
|    Service              |                         |                         |
|                         |                         |                         |
|      . ServiceID        |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Name of the service.    |
|                         |                         |                         |
|    Service              |                         |                         |
|                         |                         |                         |
|      . Name             |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Description of the      |
|                         |                         |                         |
|    Service              |                         | service.                |
|                         |                         |                         |
|      . Description      |                         |                         |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | Currency that the price |
|                         |                         |                         |
|    Currency             |                         | is in. See glossary     |
|                         |                         |                         |
|                         |                         | for list of valid       |
|                         |                         |                         |
|                         |                         | currencies.             |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | Decimal                 | Total price that needs  |
|                         |                         |                         |
|    TotalCost            |                         | to be paid. Exclude     |
|                         |                         |                         |
|                         |                         | translation credit.     |
+-------------------------+-------------------------+-------------------------+
| .. container:: notrans  | String                  | String representing the |
|                         |                         |                         |
|    DueDate              |                         | Date/Time (ISO 8601)    |
|                         |                         |                         |
|                         |                         | that the project would  |
|                         |                         |                         |
|                         |                         | be completed if         |
|                         |                         |                         |
|                         |                         | purchased right now.    |
+-------------------------+-------------------------+-------------------------+


Response Example
================

::

    <Estimate>
        <Service>
            <ServiceID>123</ServiceID>
            <Name>Machine Translation</Name>
            <Description>Service Description</Description>
        </Service>
        <Currency>EUR</Currency>
        <TotalCost>10.00</TotalCost>
        <DueDate>2014-01-25T10:32:02Z</DueDate>
    </Estimate>
