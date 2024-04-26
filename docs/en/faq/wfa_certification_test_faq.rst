WFA Certification Test
======================

:link_to_translation:`zh_CN:[中文]`

**1. How can I get the USB port number?**

  You can get it by inputting ``ls /dev/ttyUSB*`` in the command line.

**2. How can I get the MAC address of the DUT?**

  - Enter minicom and operate the command ``minicom -D /dev/ttyUSB*``
  - Input the command ``query``, and the printed ``dut_mac`` is the MAC address of the DUT.

**3. How can I flash enterprise certificate?**

  The certificate has been included in the firmware and you do not need to flash it.

**4. Why is the tool not starting?**

  Please check the Python version and ensure the toolchain is complete.

**5. Why is the tool script unable to monitor UCC command after being started?**

  Please ensure that the IP address is correctly configured on the computer.

**6. What steps should be taken if the DUT displays garbled content and is unresponsive to read or write operations?**

  Please verify whether the DUT has been flashed with the appropriate bin files and ensure that the power supply is functioning normally.