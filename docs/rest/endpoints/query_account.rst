Account query
=============

API endpoints
-------------

.. http:post:: qrylknew

   Retrieves user account information.

   .. tip:: This endpoint provides access to the user encryption key, which is required to make most authenticated API requests.

   :Request encryption: *Anonymous*
   :<json string acct: The user's account name.

   :>json string fn: The user's first name.
   :>json string ln: The user's last name.
   :>json list of user-encrypted base64 of door lock object dl: A list of the user's :http:any:`door lock <door_lock>` s.
   :>json anonymous-encrypted base64 key: The user's 3DES encryption key.

   **Example request**

   .. sourcecode:: json

      {
        "acct": "user@example.org"
      }

   **Example response**

   .. sourcecode:: json

      {
        "cod": "200",
        "fn": "John",
        "ln": "Doe",
        "dl": [
          "ZW5jcnlwdGVkX2Rvb3JfbG9ja19kYXRhX2Jhc2U2NA=="
        ],
        "rflist": [],
        "zone": "61",
        "key": "ZW5jcnlwdGVkX3VzZXJfa2V5X2Jhc2U2NA==",
        "uuid": "2a47c50c658c44a0bc123082d9bb3673",
        "rn": 2,
        "pr": [
          {
            "address": "",
            "createDate": "1660100133",
            "createDates": null,
            "id": 123456,
            "name": "Home",
            "prStatus": "O",
            "room": [
              {
                "createDate": "1660100133",
                "createDates": null,
                "id": 789012,
                "prStatus": "O",
                "propertyId": 345678,
                "roomName": "Front Door"
              }
            ]
          }
        ],
        "ct": []
      }

Data structures
---------------

.. http:any:: door_lock

   :json int propertyId: The property identifier.
   :json int roomId: The room identifier.
   :json string ID: The door lock identifier.
   :json string na: The door lock name.
   :json string tz: The door lock time zone.
   :json string hubver: The Wi-Fi hub firmare version.
   :json string mod: The Wi-Fi hub model name.
   :json string fwv: The door lock firmware version.
   :json int autoLock: The door lock auto-lock timeout, in seconds.
   :json string blename: The door lock human-readable Bluetooth name.
   :json string hubid: The Wi-Fi hub identifier.
   :json string iotdm: The Wi-Fi hub's IoT device management name.
   :json string iotsecret: The Wi-Fi hub's IoT device management secret.
   :json string iotprodkey: The Wi-Fi hub's IoT device management product key.
   :json string iothost: The Wi-Fi hub's IoT device management hostname.
   :json user object usrarr: A list of known users.

   .. sourcecode:: json

      {
        "propertyId": 123456,
        "roomId": 789012,
        "pcStatus": "Y",
        "paymentType": 0,
        "ledPush": "N",
        "secureLightInd": 0,
        "keepUnlockFlag": 0,
        "unlockStartTime": "",
        "unlockEndTime": "",
        "screenVerNum": "",
        "ID": "300030001234567890123456",
        "na": "Front Door",
        "tz": "+10:00",
        "hubver": "2.2.04.17",
        "mc": "12345678",
        "secondAdm": "N",
        "hc": "123456",
        "mod": "PGD628FN",
        "fwv": "3.02.63",
        "autoLock": 10,
        "audio": "Y",
        "pinCrazy": "N",
        "serialNum": "",
        "salesChnl": "",
        "bleSound": "Y",
        "otlkmod": 0,
        "p2pdid": "",
        "p2ppw": "",
        "gwver": "0",
        "camver": "0",
        "lkmver": "2.02.55",
        "lksver": "0",
        "blename": "LOCKLYAA00BB11",
        "sfwv": "2.02.55",
        "rfId": "",
        "camModel": "",
        "gwModel": "",
        "lockingMode": "2",
        "fpVer": "",
        "hubid": "A0B1C2D3E4F5G6H7",
        "iotdm": "M2T200112233",
        "iotsecret": "aa00bb11cc22dd33ee44ff55aa66bb77",
        "iotprodkey": "x0y1z2z3y4f",
        "iothost": "x0y1z2z3y4f.iot-as-mqtt.us-west-1.aliyuncs.com",
        "usrarr": [
          {
            "dutype": "F",
            "pid": 1,
            "fn": "John",
            "ekeyType": "",
            "ln": "Doe",
            "subadm": "N",
            "oacpriv": "N",
            "fpId": ""
          },
          {
            "dutype": "P",
            "pid": 1,
            "fn": "John Jr",
            "ekeyType": "",
            "ln": "Doe",
            "subadm": "N",
            "oacpriv": "N",
            "fpId": ""
          }
        ]
      }
