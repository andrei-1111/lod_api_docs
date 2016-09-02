=======================
Get File Translation
=======================

+---------------+----------------------------------------------+
| **Resource:** | .. container:: notrans                       |
|               |                                              |
|               |    /api/files/<<asset id>>/<<Language Code>> |
+---------------+----------------------------------------------+
| **Method:**   | .. container:: notrans                       |
|               |                                              |
|               |    GET                                       |
+---------------+----------------------------------------------+


Retrieves the translation of a file

Arguments
=========

- **Asset ID:** The onDemand Asset ID of the source file.
- **Language Code:** The locale code in the format en-us where EN is the 2 character ISO language code and US is the 2 character ISO country code.


Return Codes
============

+-------------------------+-------------------------+-------------------------+
| Status                  | Code                    | Comments                |
+=========================+=========================+=========================+
| Success                 | 200                     | Successful request      |
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
|                         |                         | account owns. Or a      |
|                         |                         |                         |
|                         |                         | translation in this     |
|                         |                         |                         |
|                         |                         | language does not exist |
|                         |                         |                         |
|                         |                         | for this file.          |
+-------------------------+-------------------------+-------------------------+
| Conflict                | 409                     | A translation has been  |
|                         |                         |                         |
|                         |                         | rejected and cannot be  |
|                         |                         |                         |
|                         |                         | retrieved until it is   |
|                         |                         |                         |
|                         |                         | fixed.                  | 
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

.. note:: If the requested translation consists of two files, they will be
          returned in a single zip file, and Range will not be supported. The
          whole file will be returned regardless of a Range header.


Errors
======

+-------------------------+-------------------------+-------------------------+
| ReasonCode              | SimpleMessage           | DetailedMessage         |
+=========================+=========================+=========================+
| 601                     | Rejected target file    | This target file was    |
|                         |                         |                         |
|                         |                         | rejected and cannot be  |
|                         |                         |                         |
|                         |                         | retrieved untile it is  |
|                         |                         |                         |
|                         |                         | fixed.                  |
+-------------------------+-------------------------+-------------------------+