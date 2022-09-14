Login
=====

API endpoints
-------------

.. http:post:: login

   Authenticates user credentials and provides an ``Authorization`` header.

   :Request encryption: *Anonymous*
   :<json string acct: The user's account name.
   :<json string password: The user's password, hashed with SHA-256.

   :>header Authorization: An authentication header to be used in future API requests.

   **Example request**

   .. sourcecode:: json

      {
        "acct": "user@example.org",
        "password": "766ef939879dc062af1cfe7bfc46f1af99a40a3926f185aee4b0801e34697c70"
      }

   **Example response**

   .. sourcecode:: json

      {
        "cod": 200,
        "msg": "success"
      }
