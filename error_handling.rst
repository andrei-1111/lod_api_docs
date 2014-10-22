==================================
Error Handling and Rate Throttling
==================================

Error Handling
==============


The onDemand API is RESTful and uses standard HTTP response codes to indicate success
and various failure states. Common HTTP status codes used by the API are:


+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| OK                      | 200                     | Returned on             |
|                         |                         |                         |
|                         |                         | succesfull get request. |
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Created                 | 201                     | Returned when a new     |
|                         |                         |                         |
|                         |                         | object (such as a quote |
|                         |                         |                         |
|                         |                         | or a file) is created.  |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Accepted                | 202                     | Returned in cases like  |
|                         |                         |                         |
|                         |                         | an accepted payment.    |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+
| Bad Request             | 400                     | This is probably        |
|                         |                         |                         |
|                         |                         | because of a malformed  |
|                         |                         |                         |
|                         |                         | request body.           |
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
| Conflict                | 409                     | This is probably        |
|                         |                         |                         |
|                         |                         | because of an invalid   |
|                         |                         |                         |
|                         |                         | parameter such as the   |
|                         |                         |                         |
|                         |                         | wrong service id or     |
|                         |                         |                         |
|                         |                         | incompatible file types.|
+-------------------------+-------------------------+-------------------------+
| System Error            | 500                     | This is probably caused |
|                         |                         |                         |
|                         |                         | by a poorly handled     |
|                         |                         |                         |
|                         |                         | exception or validation.|
|                         |                         |                         |
|                         |                         |                         |
+-------------------------+-------------------------+-------------------------+





In the case of a failure, the API will
return a data structure like this:

::
    
    <Account>
        <Status>Not Created</Status>
        <Error>
            <ReasonCode>403</ReasonCode>
            <SimpleMessage>
                This account already exists.
            </SimpleMessage>
            <DetailedMessage>
                A user with this email address already exists in the system.  
                The user should log into onDemand to find his API keys and 
                add it to the client system manually.
            </DetailedMessage>
        </Error>
    </Account>


In version 2014-06-10, the error element was broken down into three sub-elements: 

* Reason code is intended to streamline client error handling logic.
* SimpleMessage is recommended for the end user.
* DetailedMessage can be used for troubleshooting.  

Prior to the 2014-06-10 release, the Error element only contained a single message.

Here is a list of common ReasonCodes.  See the individual API pages for more details.

==========   =============================================
ReasonCode   Explanation
100          User already exists
201          Malformed product inputs
301          The number of translation credits has changed
302          The amount of prepaid credit has changed
303          Wrong quote id
304          Wrong language options
==========   =============================================


Rate Throttling
===============

To ensure optimum performance for all API consumers, The API is
throttled to 30 requests per minute per merchant.  Project creation
requests are throttled to 2 per minute per merchant.  If the client reaches the throttling
limit, the API will return a 429 response.

