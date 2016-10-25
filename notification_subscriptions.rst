==========================
Notification Subscriptions
==========================

If the quote creation request included NotificationSubscriptions, notifications
will be sent to the supplied endpoints.

Options
=======

Notification Subscriptions support different methods for how notifications will
be sent. The desired method is determined by what is supplied in the :code:`<Endpoint>`
element. We currently support POST and Email based notifications. Not all events
will support every method, however.

POST Notification Example
=========================

If the endpoint of the subscription begins with :code:`http://` or :code:`https://`, a POST
request will be sent to the supplied endpoint when the event occurs.

::

    ...
    <NotificationSubscriptions>
        <NotificationSubscription>
            <Endpoint>http://www.test.com</Endpoint>
            <EventName>quote-ready</EventName>
        </NotificationSubscription>
        <NotificationSubscription>
            <Endpoint>https://www.test.com</Endpoint>
            <EventName>quote-paid</EventName>
        </NotificationSubscription>
    </NotificationSubscriptions>
    ...


Email Notification Example
=========================

If the endpoint of the subscription begins with :code:`mailto:`, an email notification
will be sent to the supplied endpoint when the event occurs. To send the
notification to multiple email addresses, supply a comma separated list of email
addresses.

::

    ...
    <NotificationSubscriptions>
        <NotificationSubscription>
            <Endpoint>mailto:dev@lionbridge.com</Endpoint>
            <EventName>quote-ready</EventName>
        </NotificationSubscription>
        <NotificationSubscription>
            <Endpoint>mailto:dev1@lionbridge.com,dev2@lionbridge.com</Endpoint>
            <EventName>quote-paid</EventName>
        </NotificationSubscription>
    </NotificationSubscriptions>
    ...


Available Notification Subscription Events
==========================================

+-----------------------+------------------+-------------------+-----------------------------------+
| Event                 | XML Value        | Methods           | Description                       |
+=======================+==================+===================+===================================+
| .. container:: notrans| quote-ready      | POST, EMAIL       | When the quote has been priced    |
|                       |                  |                   |                                   |
|    Quote Ready        |                  |                   | and is ready for payment.         |
|                       |                  |                   |                                   |
|                       |                  |                   | See :doc:`notify_quote_ready`     |   
|                       |                  |                   |                                   |
+-----------------------+------------------+-------------------+-----------------------------------+
| .. container:: notrans| quote-paid       | POST, EMAIL       | When the quote has been paid.     |
|                       |                  |                   |                                   |
|    Quote Paid         |                  |                   | This is useful when the customer  |
|                       |                  |                   |                                   |   
|                       |                  |                   | must go to another site such as   |
|                       |                  |                   |                                   |   
|                       |                  |                   | PayPal to pay the quote balance.  |
|                       |                  |                   |                                   |
|                       |                  |                   | See :doc:`notify_quote_paid`      |
|                       |                  |                   |                                   | 
+-----------------------+------------------+-------------------+-----------------------------------+
| .. container:: notrans| project-complete | POST, EMAIL       | When a project within the quote   |
|                       |                  |                   |                                   |
|    Project Complete   |                  |                   | is completed.                     |
|                       |                  |                   |                                   |
|                       |                  |                   | See :doc:`notify_project_complete`|
|                       |                  |                   |                                   |
+-----------------------+------------------+-------------------+-----------------------------------+
