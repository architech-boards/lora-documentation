.. index:: qs

.. _quick:

Quick start guide
-----------------

In order to see working the Sensor Node Lora you have to register the device on the `activity website <http://actility.thingpark.com/portal/web>`_ clicking on **Create an account**.
After the registration login and you will access to the main page.

.. image:: _static/actility_main.jpg

First up we have to register the Microchip RN2483 device, to do this, click on **Device Manager** arrow to open a new window.

.. image:: _static/actility_device_manager.jpg

Click with the left button of the mouse on the **Devices** folder and select **+ Create**.

.. image:: _static/actility_create.jpg

In this form you have to insert the data in the following mandatory fields:

- Device EUI: the 16-hex code of the device, you can read it on the label of the board
- Network address: last 8 less significant hex from the Device EUI key
- Device profile: LoRaWAN 1.0 class A
- Network key (hexa): we have saved in the RN2834 device this one **102338F756AFBECD5647382910DAAFEB**, just for demo using.
- Application keys: we have saved in the RN2834 device this one **AFBECD56473829100192837465FAEBDC**, port 4, just for demo using.
- Connectivity plan: choose yours
- Name: insert a name just to recognize your device.

Then click on the top right **+ create**.

After the registration, you can close the window device manager and on the main page go to **Logger**.

.. image:: _static/actility_logger.jpg

Here you will see all the messages sent by your device. Now take your board:

.. image:: _static/board_bare.jpg

insert antenna and battery and keeping the board on the table switch on the Lora Sensor Node.

.. image:: _static/board_switch.jpg

Now the device is in sleeping mode, it in 30 seconds will wake up and it is going to sent a message. For skipping the sleeping phase, click on **S2** button.

.. image:: _static/board_s2.jpg

Clicking on **Refresh** button you will see the first message sent by your device. Now tilt your board to 90 degrees and wait 30 seconds.

.. image:: _static/board_tilt.jpg

The board will send another message. Now it's time to see the data sent. Power off the board. And from the logger window, you will have 2 rows, every row is a message received from the server.
If you click on the **+** node you can see the unencrypted data received **Payload (hex):**. All messages start with the number 18, the other three number couples are the data read from the accelerometer mounted on the board. You will see the data changed when you have tilted the board and sent the second message.

.. image:: _static/actility_logger2.jpg

