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
            A merchant with this information already exists in the system
        </Error>
    </CreateMerchantAccount>



Rate Throttling
===============

To ensure optimum performance for all API consumers, The API is
throttled to 30 requests per minute per merchant.  Project creation
requests are throttled to 2 per minute per merchant.

