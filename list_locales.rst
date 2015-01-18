=============
List Locales
=============

+---------------+------------------------+
| **Resource:** | .. container:: notrans |
|               |                        |
|               |    /api/locales        |
+---------------+------------------------+
| **Method:**   | .. container:: notrans |
|               |                        |
|               |    GET                 |
+---------------+------------------------+


Returns a list of all supported locales

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

The response body includes a list of locales.


+-------------------------+-------------------------+--------------------------------+
| Property                | Type                    | Comments                       |
+=========================+=========================+================================+
| .. container:: notrans  | Container               | Container of Locale information|
|                         |                         |                                |
|    Locale               |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | Common name of locale for      |
|                         |                         |                                |
|    Locale               |                         | example "English (US)"         |
|                         |                         |                                |
|      .Name              |                         |                                |
+-------------------------+-------------------------+--------------------------------+
| .. container:: notrans  | String                  | Locale code to be used in API  |
|                         |                         |                                |
|    Locale               |                         | requests.                      |
|                         |                         |                                |
|      .Code              |                         |                                |
+-------------------------+-------------------------+--------------------------------+

  

Response Example
================

::

    <Locales>
        <Locale>>
            <Name>English (US)</Name>
            <Code>en-us</Code>
        </Locale>
        <Locale>
            <Name>French (France)</Name>
            <Code>fr-fr</Code>
        </Locale>
    </Locales>

