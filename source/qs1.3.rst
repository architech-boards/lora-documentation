.. index:: qs1.3

.. _quick13:

Quick start guide for firmware 1.3
----------------------------------

This guide permits to send messages over the Lora network.

Update firmware
***************

Update your board with the lastest firmware avaiable:

1. Download the file `Lora_v13_devaddr.bin.zip <http://downloads.architechboards.com/doc/BAEVTSS002_BAEVTSS003/revB/Lora_v13_devaddr.bin.zip>`_ and unzip it.

2. Connect the board to the PC via Mini Usb cable.

.. image:: _static/board_usb.jpg

3. Go to the `mbed site <https://developer.mbed.org/handbook/Windows-serial-configuration>`_

4. Download the lastest mbed serial port driver, it is named as **mbedWinSerial**.

5. Install the driver.

6. When the driver is installed, a MBED mass storage device and a Serial line and a HID device are finded out. Open the MBED mass storage.

.. image:: _static/mbed_open.jpg

7. Copy the file **fw_devaddr.bin** into the MBED mass storage

8. The Green led on the board will blink while the file is programmed into the device flash memory

Register Module
***************

1. In order to see working the Sensor Node Lora you have to register the device on the `activity website <http://actility.thingpark.com/portal/web>`_ clicking on **Create an account**.

2. After the registration login and you will access the main page.

.. image:: _static/actility_main.jpg

3. Register your Microchip RN2483 device, to do this, click on **Device Manager** arrow to open a new window.

.. image:: _static/actility_device_manager.jpg

4. Click the right mouse button on the **Devices** folder and select **+ Create**.

.. image:: _static/actility_create.jpg

5. In this form you have to insert the data we have stored in the RN2483. The following fields are mandatory:

- **Device EUI**: the 16-hex identification key of the device. It is unique for every device, you can read it on the label of the board as in the image. For example the code can be **0004A30B001B9954**

.. image:: _static/euid_label.jpg

- **Network Address**: This is the **device address** provided by the operator, contains the NetworkID where you want to connect the device.
- **Device profile**: **LoRaWAN 1.0 class A**
- **Network key (hexa)**: we have already saved it in the RN2834 device, it is the **Device EUI** key copied *twice*, for example if the device EUI is **0004A30B001B9954** then the **network session key** you have to insert will be **0004A30B001B99540004A30B001B9954**.
- **Application keys**: Insert **AFBECD56473829100192837465FAEBDC**, port **4**. We have saved it in the RN2834 device. This is the **application sessio key**.
- **Connectivity plan**: choose yours

Optional field but useful:

- **Name**: insert a name just to recognize your device.

6. Click on the top right **+ create**.

.. warning::

    If some key is wrong then the device will be unable to send data correctly in the Lora network.

7. After the registration, you can close the window device manager and on the main page go to **Logger**.

.. image:: _static/actility_logger.jpg

8. In this page you will see all the messages sent by your device. 

Use your board
**************

Now take your board:

.. image:: _static/board_bare.jpg

The board doesn't have the correct **device address** in order to send correctly messages to your operator, so you have to set it. Follow next steps correctly:

1. Insert antenna and Micro-USB from the windows PC to the board and put the board on the table.

2. If you did not installed the mbed serial driver then go to `mbed website <https://developer.mbed.org/handbook/Windows-serial-configuration>`_ otherwise go to the step **5**

3. Download the lastest mbed serial port driver, it is named as **mbedWinSerial**.

4. Install the driver.

5. Now switch on the Lora Sensor Node.

.. image:: _static/board_switch.jpg

6. If the MBED Windows serial port driver is installed correctly Windows will recognize the board as a memory storage called MBED and as a Serial Com Port.

.. image:: _static/storage_mbed.jpg

7. Now we have to connect a terminal to the Serial Com. First step, find which number is, going to “Device Manager” and finding the node called “Ports (COM and LPT)”. In this example the number port is 170.

.. image:: _static/device_manager.jpg

8. Open a terminal like **putty**, you can find it `here <https://the.earth.li/~sgtatham/putty/latest/x86/putty.exe>`_. Launch it and set the properties signed in red in the figures:

.. image:: _static/putty_session.jpg

.. image:: _static/putty_serial.jpg

9. Press the **Open** button. Now reset the board pressing **S3** button and after keep the **S2** button pressed for 5 seconds. 

.. image:: _static/board_s2_s3.jpg

10. On the putty console you will see the starting boot text:

::

    BAEVTSS002 firmware version 1.3 - DEVADDR mode
    RN2483 1.0.1 Dec 15 2015 09:38:06

11. Keeping the **S2** button pressed you will see after some seconds the text "Please release the button S2". Now you can insert the 8 hexs **networkID** provided by your operator. After the last character inserted this value will be memorized and the text "**devaddr changed successfully**" will appear.

::

    devaddr programming mode acrived, insert 8 hexs or press Enter to exit
    DEVADDR $> 12345678
    Changing DEVADDR please wait...devaddr changed successfully

**note:** If you press Enter you can skip the procedure. 1234567 is just for example, please contact your Operator in order to know which networkID you have to use. Without the correct networkID you won't send messages with the board.

12. Now the device is in sleeping mode, in 2 minutes it will wake up and it is going to send a message. For skipping the sleeping phase, press **S2** button.

.. image:: _static/board_s2.jpg

13. After pressing **S2** button you will see the first message sent by your device. Now tilt your board to 90 degrees and wait 30 seconds.

.. image:: _static/board_tilt.jpg

14. The board will send another message. Now it's time to see the data sent. 

15. Power off the board. And in the logger window, you will have 2 rows, every row is a message received from the server.

16. If you click on the **+** node you can see the unencrypted data received **Payload (hex):**. 

17. All messages start with the number 18, the other three number couples are the data read from the accelerometer mounted on the board. You will see the data changed when you have tilted the board and sent the second message.

.. image:: _static/actility_logger2.jpg

