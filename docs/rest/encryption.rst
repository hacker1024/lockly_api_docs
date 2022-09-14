REST API encryption
===================

There are two main types of encryption used in the REST API.

Anonymous encryption
--------------------

*Anonymous* encryption is used to encrypt parts of API messages before the user encryption key is available.

Non-padded RSA is used for *anonymous* encryption. The process for both encryption and decryption is as follows:

#. Split the message bytes into chunks (64 bytes for encryption, 128 bytes for decryption).
#. Encrypt or decrypt each chunk individually using the relevant key.
#. Concatenate the encrypted chunk data, and encode the result as base64.

Encryption key
^^^^^^^^^^^^^^

*PEM, X.509 public RSA*

.. sourcecode:: pem

   -----BEGIN PUBLIC KEY-----
   MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCZtiijnvRo5EEI0n2I7shxljMX
   b7mZ/FpjuS98MHGWuYYUrsiJQVgfPn29lmI/MDkhVc7oVTsg5BIyC0TUpZKTgxyF
   DZw08AdWKe9JZvzyGB00AGkRxcem2J64xJJ04o9FW6PDLF0gSvblZAvUdHU1YyfB
   7DgJhikP7lPrFNdGwwIDAQAB
   -----END PUBLIC KEY-----

Decryption key
^^^^^^^^^^^^^^

*PEM, PKCS#8 private RSA*

.. sourcecode:: pem

   -----BEGIN PRIVATE KEY-----
   MIICdQIBADANBgkqhkiG9w0BAQEFAASCAl8wggJbAgEAAoGBAMBZug0p9CRIsZI+
   o3rMj1dlKt7AE52Ql44dSgVvaTVZ3ZWB2vRpvA80cF/QQXVbODgaU3xD0ZTkeGY6
   EP3lQaxLwGbQC1xrfLl4rVJPBt2qk0EtSQt729rOYBzMJSp0r5fPMmVDPogp3neM
   lFhP2xFlkp+yy+hsbkvXmsT9kpZjAgMBAAECgYAy0cIBJlt1lqsrq1b/47nfakA4
   V+EW2RPhnUVoSDYwvUx46rURrDnefolOFzSkL/SbhgEWrMhboT1aLO8+VWrTCF3B
   L2BPK0+G0QGYh8l56qk0dyoJiAz6Qus4OSlypNO01VIZGhNfayYlPjVlrZtDRTZF
   1kPbnUjcUwEKsrHXcQJBAOZbj4zopmYTfB7xFsbyP/K7nMOREjANLilie1Fkl8RZ
   8xSRwdz6s7r1Vx3JuUZbwyyNMG27NO+tZgdvF0u3pskCQQDVwxYUyuF+iIH9Ia2q
   Q1c1Al5fIBBUY8o7BT4tviLpQEjL2lZeJBvlRRzCyiZZISR+KXq8Id4+OKVpix6F
   oC3LAkB9z0niannezAuBFqka9NmKJ38hrEyjo78vaRLyzB67ZWkGNekMWHvqwu3W
   XgLrc1hwL5hghdsOf8R2kOzHNMFJAkA7xh+olMrVbSqcNAyx7b63DgCBrR+j2Xu1
   YVPvyplMjDNO/bDlBkfepqLSPWDXz5K6zLKLZRUWZRSsHMDeMNpdAkB1CAvpgzVt
   /OYbGvUDDK9VFbKtprN0hyFxuaX/pYaQL8hz7l+wkSvAd6lQgNlW5qLfYog06XUe
   xrOFRvMjIhMm
   -----END PRIVATE KEY-----

User encryption
---------------

*User* encryption is used to encrypt parts of API messages after the user encryption key is available.

The Triple Data Encryption Algorithm (3DES) with PKCS#7 padding is used for *user* encryption.

The key used is (potentially) unique to each user.

.. tip:: The *user* encryption key can be obtained using the :doc:`account query API</rest/endpoints/query_account>`.

.. tip:: 3DES is a symmetric cipher. This makes reverse-engineering much of the Lockly app with a packet sniffer possible.
