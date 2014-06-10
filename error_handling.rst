==================================
Error Handling and Rate Throttling
==================================

Error Handling
==============


The onDemand API uses standard HTTP response codes to indicate success
and various failure states.  In the case of a failure, the API will
return a data structure like this:

::
    
    <CreateMerchantAccount>
        <Status>Not Created</Status>
        <Error>
            <ReasonCode>1</ReasonCode>
            <SimpleMessage>
                This account already exists.
            </SimpleMessage>
            <DetailedMessage>
                A user with this email address already exists in the system.  
                The user should log into onDemand to find his API keys and 
                add it to the client system manually.
            </DetailedMessage>
        </Error>
    </CreateMerchantAccount>


In version 2014-06-10, the error element was broken down into three sub-elements: 

* Reason code is intended to streamline client error handling logic.
* SimpleMessage is recommended for the end user.
* DetailedMessage can be used for troubleshooting.  

Prior to the 2014-06-10 release, the Error element only contained a single message.

===========  ==============================================
ReasonCode   Explanation
100          User already exists
201          Malformed product inputs
301          The number of translation credits has changed
302          The amount of prepaid credit has changed
303          Wrong quote id
304          Wrong language options 


Rate Throttling
===============

To ensure optimum performance for all API consumers, The API is
throttled to 30 requests per minute per merchant.  Project creation
requests are throttled to 2 per minute per merchant.  If the client reaches the throttling
limit, the API will return a 429 response.

