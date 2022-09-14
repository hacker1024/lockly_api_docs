REST API
========

This is the entrypoint to the REST API documentation.

The REST API is used by the Lockly app to manage user accounts and locks.

.. tip::
   
   | Have a read through the general documentation section to get started.
   | Then, move on to logging in, and obtaining a user encryption key through the account query API.

.. toctree::
   :caption: General documentation
   :maxdepth: 2

   api_format
   encryption

.. toctree::
   :caption: Endpoints
   :maxdepth: 1
   :glob:

   endpoints/*
