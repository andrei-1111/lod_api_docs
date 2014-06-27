=======================
Lionbridge onDemand API
=======================

**Version:** 2014-02-28*


The Lionbridge onDemand API is a RESTful programming interface to Lionbridge's onDemand Translation Service.  Using the API, client applications can submit content to Lionbridge for translation.  The API can be used against the onDemand Retail site or onDemand Enterprise. 

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
   reject_quote
   notification 
   list_projects
   get_project
   list_products
   get_product
   get_product_translation
   list_services
   get_terms
 
   

Getting Help
============

The Lionbridge onDemand integration support team is eager to help you be successful with your integration.
The best way to reach them is through the `onDemand Support Portal <https://support.liondemand.com/>`_. 
There you will find support articles and a form to submit a support ticket.


Getting API Keys
================

You can get API keys on our `sandbox server <https://demo.liondemand.com/>`_ by registering for an account and then visiting the `profile page <https://demo.liondemand.com/user/profile/>`_ to create your API keys.

.. image:: /_static/img/api_keys.png
   :alt: alternate text
   :align: center

If you have trouble getting your API keys or need an account on an enterprise site sandbox, please contact `support <https://support.liondemand.com/>`_.


High Level Workflow
===================

This high level sequence diagram shows the workflow for creating and completing onDemand projects.  The process starts with the merchant building list of projects to translate within the client application.  Then the merchant selects a service and target languages and requests a quote.  onDemand responds with a quote that contains information about how the work will be broken down into projects and pricing information.  The merchant can authorize the quote (and if necessary pay) to start the project.  


.. image:: /_static/img/high_level_workflow_sequence.png
   :alt: alternate text
   :align: center


Glossary
========

This is list of terminology used in this document.

* Currency. Lionbridge onDemand currently supports the following 4 currencies: CAD (Canadian Dollars), EUR (Euros), GBP (Great Britain Pound Sterling), USD (US Dollars).  
* LanguageCode.  A locale code in the format en-us where EN is the 2 character ISO language code and US is the 2 character ISO country code.
* Product. A product SKU to be translated.
* Project. Like items are grouped into a Project and delivered to the translation system.  Translation completion notifications is done at the project level.  For translation efficiency, all products in project must be in the same top level category and have the same language and quality settings.
* Service.  A service defines pricing and quality level for a project.
* Quote. A quote maps to a transaction which can include 1 or more projects.  



   
