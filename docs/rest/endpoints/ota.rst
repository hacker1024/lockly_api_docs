OTA
===

API endpoints
-------------

.. http:post:: lockly/syspara

   Retreives OTA update information.

   :Request encryption: *None*
   :json string did: The door lock identifier. See also: :http:post:`qrylknew`.
   :json string mod: The Wi-Fi hub model name. See also: :http:post:`qrylknew`.
   :json string ref: The user's account name.

   **Example request**

   .. sourcecode:: text

      firmware_ver

   **Example response**

   .. sourcecode:: json

      {
        "cod": "200",
        "para": "firmware_ver",
        "value": "3.02.63",
        "short_desc": "55",
        "long_desc": "http://apiserv001.pin-genie.com/firmware/PGD628FN_firmware_V3.02.63_4E20FF.bin",
        "AlertLevel": 0,
        "title": "",
        "content": "",
        "guide": "http://image.pin-genie.com/lock/guide/ogl_rain_welcome.html",
        "minv": "",
        "notify": "N"
      }
