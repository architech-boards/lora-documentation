.. index:: hardware

.. _hardware:

Hardware Guide
--------------

The board is provided with:

- NXP MKL26Z microprocessor
- NXP MK20DX128VFM5 microprocessor
- Microchip RN2483 Module
- Light Sensor
- Reset button
- Wake-up button
- NXP FXOS8700CQR1 Accelerometer and Magnetometer sensor
- LEDs which one is used directly by KL26Z

The Microchip RN2483 module provides LoRaWAN™ protocol connectivity using a simple UART interface. The NXP **MKLS26Z** is connected to the Microchip modules using the configuration 57600 8N1 without using RTS, CTS lines. Last version used is **1.0.1**.

The Light Sensor is read from the ADC converter peripheral of the MKL26Z.

The Accelerometer sensor is read from I2C interface.

The microcontroller uses the deep sleep mode **VLPS**, it is waken up by LPTimer every 30 seconds or by pin interrupt connected to the **S2** button.

Configuration RN2483
********************

The connection used by **RN2483** is **ABP** (Activation by Personalization). To use this connection it is required to setup the RN device only one time. Every Lora Sensor Node bought is already configured. The commands used were:

 | sys factoryRESET
 | sys get hweui
 | mac set deveui [hweui key read]
 | mac set devaddr [last less significant hexs of hweui key]
 | mac set appskey AFBECD56473829100192837465FAEBDC
 | mac set nwkskey [hweui key repeated two times]
 | mac save

After saving this setup is not required repeat the opeation of setup. In order to send data in the Lora network the two used commands are:

- **mac join abp**: used to join the Lora network

- **mac tx cnf 4 18AABBCC48DD0000**: used to send the frame *"18AABBCC48DD0000"* on the port 4

Datasheet and more
******************

Please refer to `architechboards <http://architechboards.org/>`_ website.

.. image:: _static/logo_architech.jpg

