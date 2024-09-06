RF Testing FAQs
===============

:link_to_translation:`zh_CN:[中文]`

**1. What should I do if the EspRFTestTool Toolkit fails to flash?**

   The chip might not have entered download mode correctly. Follow these steps to troubleshoot:

   - Check the log: Use a serial tool (such as sscom, `Serial Port Utility <http://alithon.com/downloads>`__), select the correct baud rate, and check the log after powering up the chip.

   - Confirm download mode: When the chip enters download mode, it typically displays "wait for download."

   - Check the connections: If no log is printed, ensure that the power supply and UART connections are functioning properly.

**2. How can I confirm whether the firmware was successfully flashed?**

    Even if the flashing tool indicates success, the firmware might not have been flashed correctly. Follow these steps to verify:

    - Check the log: Close the serial port used by the flashing tool, open a serial tool (such as sscom, `Serial Port Utility <http://alithon.com/downloads>`__), select the correct baud rate, and check the log.

    - Enter working mode: Pull up the Boot pin and re-power the chip to enter working mode.

    - Confirm flash success: Check if the log shows continuous reboots or matches the expected behavior based on the firmware documentation to confirm if the flashing was successful.

**3. What should I do if the running traffic fails in the Wi-Fi Adaptivity Test?**

    If running traffic fails, consider the following possible causes and solutions:

    - Firmware issues: Ensure that the firmware was flashed successfully.

    - Network issues: Check whether the router (AP) network is stable and connections are smooth.

    - Connection delays: If the connection is slow, wait a few seconds and restart running traffic.

    - Serial testing: If the issue persists, consider testing via serial commands.
