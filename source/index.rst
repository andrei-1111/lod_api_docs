Welcome to the Lionbridge onDemand API!
=======================================
The Lionbridge onDemand API is a RESTful programming interface to Lionbridge's onDemand Translation Service.  Using the API, client applications can submit content to Lionbridge for translation.  The API can be used against the onDemand Retail site or onDemand Enterprise.  

.. toctree::
   :maxdepth: 1

   create_account

.. toctree::
   :maxdepth: 2

   release_notes/index


Getting Help
============



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




   
