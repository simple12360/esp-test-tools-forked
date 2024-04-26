Flash Download Tool
===================

:link_to_translation:`zh_CN:[中文]`

**1. I cannot find the serial port that I am using in the COM drop-down menu when I open the Flash Download Tool.**

First go to the device manager and check if the serial port has been successfully installed. If not, check the driver for any possible issues.

**2. I get the "COM FAIL" error message, as shown in the Figure below:**

.. figure:: ../../_static/flash_download_tool/serial_port_connection_failure.jpg
    :align: center
    :scale: 90%

    Connection Failure of Serial Port

- Firstly, make sure the selected COM is correct
- Then, check if the COM is already occupied by another thread.

**3. The Flash Download Tool is stuck at the step shown in the figure below. How can I fix this?**

.. figure:: ../../_static/flash_download_tool/download_panel.jpg
    :align: center
    :scale: 90%

This may happen for the reasons given below

- Hardware: The module is not in download mode.
- Software: The module selected in the tool is not the one you are actually using.

**4. I click the START button, and get the error shown in the figure below.**

.. figure:: ../../_static/flash_download_tool/efuse_error.jpg
    :align: center
    :scale: 90%

You will get the ``ESP8266 Chip efuse check error esp_check_mac_and_efuse`` message when there are errors related to the eFuse. The possible causes are as follows:

- The eFuse is OK, but the module selected in the tool is not the one that is actually being used. In this situation, please select the module type based on your actual case.
- There are problems with the eFuse of the module. In this case, please contact Espressif to obtain the required esptool.exe and operating instructions. Also, send the data that is read from eFuse to Espressif for further debugging.

**5. Errors occur during downloading.**

Please check the following:

- The TX/RX of the module is not used by other software programs.
- The module flash size is no less than the size of firmware to be downloaded.
- If there is an MD5 verification error, erase the entire flash and try downloading again.

**6. The module crashes when powered on again after the firmware has been downloaded.**

If the downloaded firmware works fine, then please check the following:
- The module selected in the tool is not the one you are actually using.
- The selected flash boot mode is wrong.
- The selected flash download mode is wrong.