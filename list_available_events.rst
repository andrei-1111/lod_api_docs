=========================
List Notification Events
=========================

+---------------+------------------------------+
| **Resource:** | .. container:: notrans       |
|               |                              |
|               |    /api/notification-events  |
+---------------+------------------------------+
| **Method:**   | .. container:: notrans       |
|               |                              |
|               |    GET                       |
+---------------+------------------------------+

Returns a list of all notification events a user can subscribe to.

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

The response body includes a list of notification event names and their
supported methods.


+---------------------------+-------------------------+----------------------------+
| Property                  | Type                    | Comments                   |
+===========================+=========================+============================+
| .. container:: notrans    | Container               | Container of Event Type    |
|                           |                         |                            |
|    EventType              |                         | information                |
+---------------------------+-------------------------+----------------------------+
| .. container:: notrans    | String                  | Name of event that can be  |
|                           |                         |                            |
|    EventType              |                         | subscribed to.             |
|                           |                         |                            |        
|       .EventName          |                         |                            |
+---------------------------+-------------------------+----------------------------+
| .. container:: notrans    | Container               | Container of Notification  |
|                           |                         |                            |
|    EventType              |                         | Method information         |
|                           |                         |                            |
|       .NotificationMethods|                         |                            |
+---------------------------+-------------------------+----------------------------+
| .. container:: notrans    | String                  | Name of method that can be | 
|                           |                         |                            |
|    EventType              |                         | used to send notification  |
|                           |                         |                            |
|       .NotificationMethods|                         |                            |
|                           |                         |                            |
|       .NotificationMethod |                         |                            |
+---------------------------+-------------------------+----------------------------+


Response Example
================

::

    <EventTypes>
      <EventType>
        <EventName>quote-ready</EventName>
        <NotificationMethods>
          <NotificationMethod>email</NotificationMethod>
          <NotificationMethod>http-post</NotificationMethod>
        </NotificationMethods>
      </EventType>
      <EventType>
        <EventName>project-complete</EventName>
        <NotificationMethods>
          <NotificationMethod>email</NotificationMethod>
          <NotificationMethod>http-post</NotificationMethod>
        </NotificationMethods>
      </EventType>
      <EventType>
        <EventName>quote-paid</EventName>
        <NotificationMethods>
          <NotificationMethod>email</NotificationMethod>
          <NotificationMethod>http-post</NotificationMethod>
        </NotificationMethods>
      </EventType>
    </EventTypes>

