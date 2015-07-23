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
| Partial Content         | 206                     | Range requested was     |
|                         |                         |                         |
|                         |                         | returned                |
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
| Gone                    | 410                     | The files have gone     |
|                         |                         |                         |
|                         |                         | past their retention    |
|                         |                         |                         |
|                         |                         | period                  |
+-------------------------+-------------------------+-------------------------+

Response Body
=============

The response body is the contents of the file (or specified range of file when
making a range request).


Range Request
=============

It is possible to request only a particular portion of the file by sending a
properly formed HTTP Range header, a la ``Range: bytes=500-999`` where ``500``
is the first byte desired (0-based), ``999`` is the last bite desired.
