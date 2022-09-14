Bluetooth communication
=======================

API endpoints
-------------

.. http:post:: asyncSend

   Sends a raw Bluetooth Low Energy packet to the lock via the Wi-Fi hub.

   .. tip:: Many of the actions done by the Lockly app over Wi-Fi are implemented through the use of this endpoint.

   :Request encryption: *User*
   :<json string acct: The user's account name.
   :<json string cmd: The BLE packet, in a hexadecimal encrypted form.
   :<json string dv: The door lock identifier. See also: :http:post:`qrylknew`.
   :<json string mdna: The Wi-Fi hub's IoT device management name. See also: :http:post:`qrylknew`.

   :>json string req_msg_id: The request message ID. Used in MQTT messages.

   **Example request**

   .. sourcecode:: json

      {
        "acct": "user@example.org",
        "cmd": "aa00bb11cc22dd33ee44ff55aa00bb11cc22dd33ee44ff55aa00bb11cc22dd33ee44ff55aa00bb11",
        "directive": "lock",
        "dv": "300030001234567890123456",
        "mdna": "M2T200112233"
      }

   **Example response**

   .. sourcecode:: json

      {
        "cod": "200",
        "req_msg_id": 1590073500295600300
      }
