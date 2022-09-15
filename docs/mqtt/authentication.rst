Connecting to the MQTT broker
=============================

Obtaining MQTT details
----------------------

The MQTT details for each Wi-Fi hub can be found in the :http:any:`door_lock` data.

Specifically, the following fields are used:

- ``iotprodkey``: The Wi-Fi hub's IoT device management product key
- ``iotdm``: The Wi-Fi hub's IoT device management name
- ``iotsecret`` The Wi-Fi hub's IoT device management secret
- ``iothost``: The MQTT broker host (``{iodprodkey}.iot-as-mqtt.cn-shanghai.aliyuncs.com`` if unprovided)

Authenticating with the MQTT broker
-----------------------------------

The `Alibaba Cloud IoT Platform documentation <https://www.alibabacloud.com/help/en/iot-platform/latest/establish-mqtt-connections-over-tcp>`_ describes the MQTT credential format.

================= ============== ===============
Alibaba parameter Lockly vaue    Customizable
================= ============== ===============
securemode        ``"2"``        Yes
signmethod        ``"hmacsha1"`` Yes
deviceName        ``iotdm``      No
productKey        ``iotprodkey`` No
deviceSecret      ``iotsecret``  No
================= ============== ===============

The **mqttUsername** is used as the **clientId**.
