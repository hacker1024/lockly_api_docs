REST API format
===============

Endpoints
---------

REST API requests are made to the following endpoints:

.. http:any:: https://apiserv03c.lockly.com/pgsmtlkv2/api/(string:endpoint)
.. http:any:: https://apiserv04c.lockly.com/(string:endpoint)

All documented endpoints use the first listed endpoint, unless stated otherwise.

Message format
--------------

All API messages follow the following format.

JSON request fields in the endpoint documentation refer to the contents of the ``para`` field.

.. http:any:: (string:endpoint)

   :<header Authorization: An authorization header obtained through the :doc:`login </rest/endpoints/login>` process.
   :<header Content-Type: Always ``application/json``.
   :<json string ctry: The locale of the app, obtained with `Locale.getCountry <https://developer.android.com/reference/java/util/Locale#getCountry()>`_ on Android (e.g. ``AU``).
   :<json string dvid: A persistent randomly-generated lowercase v4 UUID with no dashes (e.g. ``d23a84a871f24f088d0e04887344d71a``).
   :<json string locale: The locale of the app (e.g. ``EN`` or ``EN_GB``).
   :<json string os: The operating system of the app (e.g. ``android``).
   :<json string or base64 para: Request parameters - often :doc:`encrypted <encryption>`.
   :<json string rid1: A Firebase Cloud Messaging token.
   :<json string rid2: A Mi Push token.
   :<json string tk: A password (used in only a few API requests).
   :<json string ver: The app version code (e.g. ``237``).
   :<json string versionName: The app version name (e.g. ``2.3.7``).

   :>json int or stringified int cod: An error code. 200 is a success. Note that this is not an HTTP status code.
   :>json optional string msg: A message describing the result of the API request.

   Other top-level request parameters may be required for some endpoints. These will be documented as general JSON parameters, like so:

   :json string toplevelParameter: A top-level (not part of ``para``) parameter.
   :<json string regularParameter: A regular parameter in ``para``.


   .. warning:: Make sure to include the ``Content-Type`` header in all API requests. Ommiting it will result in unusual errors.

   .. warning:: The ``cod`` response field can be either an integer or a string - make sure to handle both cases.
