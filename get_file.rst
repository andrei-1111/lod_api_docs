=============
Get File
=============

+---------------+----------------------------+
| **Resource:** | .. container:: notrans     |
|               |                            |
|               |    /api/files/<<asset id>> |
+---------------+----------------------------+
| **Method:**   | .. container:: notrans     |
|               |                            |
|               |    GET                     |
+---------------+----------------------------+


Returns a source file

Arguments
=========

- **Asset ID:** The onDemand Asset ID.  You will receive this ID from :doc:`get_project`


Return Codes
============

+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Success                 | 200                     | Successful request      |
+-------------------------+-------------------------+-------------------------+
| No Content              | 204                     | The files are not yet   |
|                         |                         |                         |
|                         |                         | ready                   |
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
|                         |                         | account owns.           |
+-------------------------+-------------------------+-------------------------+
| Gone                    | 410                     | The files have gone     |
|                         |                         |                         |
|                         |                         | past their retention    |
|                         |                         |                         |
|                         |                         | period                  |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body is the contents of the file.


