=======================
Get File Translation
=======================

=============  ============================================
**Resource:**  /api/files/<<asset id>>/<<Language Code>>
**Method:**    GET
=============  ============================================

Retrieves the translation of a file


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
|                         |                         | to a file that the      |
|                         |                         |                         |
|                         |                         | account owns. Or a      |
|                         |                         |                         |
|                         |                         | translation in this     |
|                         |                         |                         |
|                         |                         | language does not exist |
|                         |                         |                         |
|                         |                         | for this file.          |
+-------------------------+-------------------------+-------------------------+


Response Body
=============

The response body is the contents of the file.

