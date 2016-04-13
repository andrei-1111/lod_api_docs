==================
Accept File Translation
==================

+---------------+-------------------------------------------------------------------+
| **Resource:** | .. container:: notrans                                            |
|               |                                                                   |
|               |   /api/files/<<asset id>>/<<language code>>/accept/               |
+---------------+-------------------------------------------------------------------+
| **Method:**   | .. container:: notrans                                            |
|               |                                                                   |
|               |    POST                                                           |
+---------------+-------------------------------------------------------------------+

This API is used to explicitly accept translated files. 

Request Body
============

Empty


Response Body
=============

Empty


Return Codes
============

+--------------+------+-------------------------+
|    Status    | Code |         Comments        |
+==============+======+=========================+
| Success      |  202 | Successful request      |
+--------------+------+-------------------------+
| Unauthorized |  401 | The request did not     |
|              |      | pass authentication or  |
|              |      | the customer is not a   |
|              |      | member of an enterprise |
|              |      | site.                   |
+--------------+------+-------------------------+
| Not Found    |  404 | No matching document    |
|              |      | found                   |
+--------------+------+-------------------------+
