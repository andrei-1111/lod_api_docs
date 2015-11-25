=======================================
Lionbridge Content API (V. 2015-02-23)
=======================================

The Lionbridge Content API is a RESTful programming interface to Lionbridge's onDemand Translation Service.  With the Lionbridge Content API you can:

- Create onDemand buyer accounts using :doc:`create_account`.
- Find the most cost-effective translation quality level for your content using :doc:`list_services`.
- Create translation projects using :doc:`generate_quote`.
- Get a notification when your project is done.


The API can be used against the `Lionbridge onDemand Retail site <https://ondemand.lionbridge.com>`_ or an `Lionbridge onDemand Enterprise <http://info.lionbridge.com/onDemand-Enterprise.html>`_ site. Scroll down for a :ref:`high_level_workflow`


**Version:** 2015-02-23 *Latest*

Earlier Releases:

- `Version 2014-09-04 <./archive/2014-09-04/>`_
- `Version 2014-06-10 <./archive/2014-06-10/>`_
- `Version 2014-02-28 <./archive/2014-02-28/>`_



New in This Release
===================

- Responses from GenerateQuote now include ``<Project/>`` data, to be more
  consistent with other quote responses.
- Responses from GenerateQuote and GetQuote have been homogenized. Previously
  GetQuote did not return as much information as GenerateQuote, and it was not
  always possible to authorize a quote with that data.


Contents
========


.. toctree::
   :maxdepth: 1

   authentication
   error_handling
   create_account
   account_information
   add_prepaid_balance
   generate_quote
   authorize_quote
   get_quote
   list_quotes
   reject_quote
   notify_project_complete
   notify_quote_ready
   notify_quote_paid
   add_project
   list_projects
   get_project
   add_file
   add_file_by_reference
   list_files
   get_file
   get_file_details
   get_file_translation
   list_products
   get_product
   get_product_translation
   list_services
   get_service
   get_estimate
   list_locales
   get_terms



Getting Help
============

The Lionbridge Content API integration support team is eager to help you be successful with your integration.
The best way to reach them is through the `onDemand Support Portal <https://support.liondemand.com/>`_.
There you will find support articles and a form to submit a support ticket.

Libraries and Sample Code
=========================

PHP developers will find `this sample code by Andrey Artiushenko <https://github.com/workaandrey/ondemand-php-sdk>`_  helpful. You can import it into your project and use it as is or just borrow the bits that deal with authenticating requests.

`Dan Spector <https://www.linkedin.com/in/danspector03>`_ has written an `onDemand API client library in C# <https://github.com/DanSpector/lionbridge-ondemand-client-csharp>`_ for .NET developers. This library is very actively used in the `Clay Tablet <http://clay-tablet.com>`_ connector for onDemand.


Getting API Keys
================

You can get API keys on our `sandbox server <https://demo.liondemand.com/>`_ by registering for an account and then visiting the `profile page <https://demo.liondemand.com/user/profile/>`_ to create your API keys.

.. image:: /_static/img/api_keys.png
   :alt: alternate text
   :align: center

If you have trouble getting your API keys or need an account on an enterprise site sandbox, please contact `support <https://support.liondemand.com/>`_.

.. _high_level_workflow:

High Level Workflow
===================


This high level sequence diagram shows the workflow for creating and completing onDemand projects.  The process starts with an end user building list of content assets to translate within the client application.  Then the merchant selects a service and target languages and requests a quote.  onDemand responds with a quote that contains information about how the work will be broken down into projects and pricing information.  The end user can authorize the quote (and if necessary pay) to start the project.


.. image:: /_static/img/high_level_workflow_sequence.png
   :alt: alternate text
   :align: center


1. The end user uses the client application to build a list of content to be translated. These assets can be products or files.
2. The end user selects an option to translate the selected assets and is presented a list of translation services that are available.  Typically, these translation services will represent different quality levels such as straight machine translation, machine translation with human post edit, crowd translation, professional translation, and specialist domain translation.  The list of avialable services can be found by calling the :doc:`list_services` API.
3. The end user submits the list of content assets for a quote.
4. If the project is file-based, the client application uploads each file using the :doc:`add_file` API.  If the project is product-based, the products are sent to onDemand when generating the quote.
5. The client application calls the :doc:`generate_quote` API to build a quote for the selected content and translation service.  Product-based projects and some file-based products will come back immediately with a completed quote containing a price. Other quotes will require additional time to parse the files.
6. If the price is not ready, the quote will come back with a status of calculating and no price.  If this is the case, the client application should regularly call the :doc:`get_quote` API until the quote is "Pending" or has a status of "Error."
7. The client application should notify the end user that the price is ready.
8. The end user can authorize or reject the quote.
9. The client application calls either the :doc:`authorize_quote` or :doc:`reject_quote` API depending on the end user's preference. If the end user has a prepaid balance or has been given free translation credit, authorizing the quote will automatically start the translation projects.  If funds are required, the end user must go through a payment process.
#. If payment is required, the authorize quote request will come back with an HTTP status code of 402.  The body of the response will contain a PaymentURL that the end user can follow to submit payment.
#. The client application sends the end user to the payment page where he or she can pay for the balance due.
#. Lionbridge will complete the projects and notify the client application that the translated content is ready.



Glossary
========

This is list of terminology used in this document.

* Currency. Lionbridge onDemand currently supports the following 4 currencies: CAD (Canadian Dollars), EUR (Euros), GBP (Great Britain Pound Sterling), USD (US Dollars).
* LanguageCode.  A locale code in the format en-us where EN is the 2 character ISO language code and US is the 2 character ISO country code.
* Product. A product SKU to be translated.
* Project. Like items are grouped into a Project and delivered to the translation system.  Translation completion notifications is done at the project level.  For translation efficiency, all products in project must be in the same top level category and have the same language and quality settings.
* Service.  A service defines pricing and quality level for a project.
* Quote. A quote maps to a transaction which can include 1 or more projects.




