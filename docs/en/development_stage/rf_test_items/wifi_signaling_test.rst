Wi-Fi Signaling Test
====================

:link_to_translation:`zh_CN:[中文]`

The Wi-Fi Signaling Test assesses and verifies the Wi-Fi signaling functions of wireless network devices, focusing on stable and reliable communication across varying operating scenarios. It evaluates Over-The-Air (OTA) performance, including Total Radiated Power (TRP) and Total Isotropic Sensitivity (TIS).

Set Up Test Environment
-----------------------

.. figure:: ../../../_static/rf_test_tool/usb_to_uart_connection.png
    :align: center
    :scale: 80%

    UART Connection Description

The **Device Under Test (DUT)** is a product designed based on Espressif chips or modules. The device under test is connected to the USB-to-UART adapter board via UART.

.. note::

    - The CHIP_EN pin of the device under test is pulled up by default. If it is not pulled up in the product design, you need to manually connect the CHIP_EN to the 3V3 pin.
    - Some serial communication boards have already swapped RXD and TXD internally, so there is no need to reverse them. The wiring needs to be adjusted according to the actual situation.
    - Espressif chips have a power-on self-calibration feature. Therefore, before powering on the device under test, the RF connection cable must be connected to the testing instrument.

Flash Firmware
--------------

{IDF_TARGET_WIFI_SIGNALLING_SINGLE_FIRMWARE:default="Not updated", esp32="|ESP32 Wi-Fi Signaling Test Firmware (Single Country)|", esp32c2="|ESP32-C2 Wi-Fi Signaling Test Firmware (Single Country)|", esp32c6="|ESP32-C6 Wi-Fi Signaling Test Firmware (Single Country)|", esp32c3="|ESP32-C3 Wi-Fi Signaling Test Firmware (Single Country)|"}

{IDF_TARGET_WIFI_SIGNALLING_MULTIPLE_FIRMWARE:default="Not updated", esp32="|ESP32 Wi-Fi Signaling Test Firmware (Multiple Countries)|", esp32c2="|ESP32-C2 Wi-Fi Signaling Test Firmware (Multiple Countries)|", esp32c6="|ESP32-C6 Wi-Fi Signaling Test Firmware (Multiple Countries)|", esp32c3="|ESP32-C3 Wi-Fi Signaling Test Firmware (Multiple Countries)|"}

{IDF_TARGET_FLASH_ADDRESS:default="0x0", esp32="0x1000", esp32s2="0x1000"}

1. Open :ref:`download-tool`.

2. Set ``ChipType``, ``Com Port`` and ``Baud Rate``, click ``Open``, and select download to ``Flash``.

3. {IDF_TARGET_WIFI_SIGNALLING_SINGLE_FIRMWARE} supports a single country code, {IDF_TARGET_WIFI_SIGNALLING_MULTIPLE_FIRMWARE} supports multiple country codes. They each include 4 bin files, i.e., **bootloader.bin**, **partition-table.bin**, **phy_init_data.bin**, and **ssc.bin**.

After unzipping {IDF_TARGET_WIFI_SIGNALLING_SINGLE_FIRMWARE} or {IDF_TARGET_WIFI_SIGNALLING_MULTIPLE_FIRMWARE}, flash the 4 bin files to the following addresses via UART.

.. list-table::
   :header-rows: 1

   * - bin file
     - flashing address
   * - bootloader.bin
     - {IDF_TARGET_FLASH_ADDRESS}
   * - partition-table.bin
     - 0x8000
   * - phy_init_data.bin
     - 0xF000
   * - ssc.bin
     - 0x10000

.. only:: esp32 or esp32s2

    .. figure:: ../../../_static/rf_test_tool/wifi_signaling_firmware_esp32_esp32s2.png
        :align: center
        :scale: 80%

        Firmware Flashing Schematic

.. only:: not esp32 and not esp32s2

    .. figure:: ../../../_static/rf_test_tool/wifi_signaling_firmware_others.png
        :align: center
        :scale: 80%

        Firmware Flashing Schematic

After the flashing is completed, continue with the following steps for signaling testing.

.. _wifi-signalling-test:

Start Testing
-------------

Check Power-on Log
^^^^^^^^^^^^^^^^^^

Use a serial communication tool such as `Serial Port Utility <http://alithon.com/downloads>`__ to configure the port number and set the baud rate to 115200. After the device is powered on again, if the serial port outputs information similar to the following, you can confirm that the test status is OK:

.. figure:: ../../../_static/rf_test_tool/esp32c2_wifi_signaling.png
    :align: center
    :scale: 80%

    Serial Port Log for Device Power-on

Device Provisioning
^^^^^^^^^^^^^^^^^^^

Enter the following two commands in the serial port in sequence for network configuration.

::

  //Device Provisioning
  //Configure the prototype to enter station mode
  op -S -o 1

  //Connect to AP, SSID is CMW-AP, password is 12345678
  sta -C -s CMW-AP -p 12345678

.. note::

    The ``-p`` parameter is used to set the AP password. If the AP has no password, this parameter is not needed.

After the station device is assigned an IP address, the Wi-Fi connection is successful, and the following log is printed:

.. figure:: ../../../_static/rf_test_tool/esp32c2_wifi_signaling_connection.png
    :align: center
    :scale: 80%

    Serial Port Log for Device Provisioning

After the device under test is successfully connected, you can use the RF test instrument for Wi-Fi Signaling Test.


.. |ESP32 Wi-Fi Signaling Test Firmware (Single Country)| replace:: `ESP32 Wi-Fi Signaling Test Firmware (Single Country) <https://dl.espressif.com/rf/esp32/ESP32ECO3_Signaling_V4.3_SinglePhy_20230525.zip>`__

.. |ESP32-C2 Wi-Fi Signaling Test Firmware (Single Country)| replace:: `ESP32-C2 Wi-Fi Signaling Test Firmware (Single Country) <https://dl.espressif.com/RF/ESP32C2_v5.0_e255ce0_26M_singlephy_20250430.zip>`__

.. |ESP32-C3 Wi-Fi Signaling Test Firmware (Single Country)| replace:: `ESP32-C3 Wi-Fi Signaling Test Firmware (Single Country) <https://dl.espressif.com/RF/ESP32C3_v5.5_402fb258_singlephy_20250722.zip>`__

.. |ESP32 Wi-Fi Signaling Test Firmware (Multiple Countries)| replace:: `ESP32 Wi-Fi Signaling Test Firmware (Multiple Countries) <https://dl.espressif.com/rf/esp32/ESP32ECO3_Signaling_V4.3_MultiPhy_20230525.zip>`__

.. |ESP32-C2 Wi-Fi Signaling Test Firmware (Multiple Countries)| replace:: `ESP32-C2 Wi-Fi Signaling Test Firmware (Multiple Countries) <https://dl.espressif.com/RF/ESP32C2_v5.0_e255ce0_26M_multiphy_20250430.zip>`__

.. |ESP32-C3 Wi-Fi Signaling Test Firmware (Multiple Countries)| replace:: `ESP32-C3 Wi-Fi Signaling Test Firmware (Multiple Countries) <https://dl.espressif.com/RF/ESP32C3_v5.5_402fb258_multiphy_20250722.zip>`__

.. |ESP32-C6 Wi-Fi Signaling Test Firmware (Single Country)| replace:: `ESP32-C6 Wi-Fi Signaling Test Firmware (Single Country) <https://dl.espressif.com/RF/ESP32-C6_v5.4.2_d12e5a3_SinglePhy_20250808.zip>`__

.. |ESP32-C6 Wi-Fi Signaling Test Firmware (Multiple Countries)| replace:: `ESP32-C6 Wi-Fi Signaling Test Firmware (Multiple Countries) <https://dl.espressif.com/RF/ESP32-C6_v5.4.2_d12e5a3_MultiplePhy_20250808.zip>`__
