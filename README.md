# NORVI GSM-AE08-I-L -- Hardware Test Example

## Overview

This example demonstrates how to run a hardware test on the NORVI
GSM-AE08-I-L controller.

The purpose of this example is to show how to:

-   Start the Wi-Fi access point and print the device MAC address
-   Initialize the OLED display, RTC, microSD card and Ethernet
-   Test the GSM modem using AT commands
-   Send test data over RS-485
-   Read the status of the 4 digital inputs
-   Read the 4 analog input channels

This example can be used as a starting point for developers building
applications with NORVI controllers.

## Product Used

Product: NORVI GSM-AE08-I-L\
Platform: Arduino IDE / PlatformIO (ESP32)

<https://norvi.io>

## Purpose of This Example

The example demonstrates how to:

-   Start a Wi-Fi access point named after the device MAC address
-   Read the DS3231 RTC and print the date and time
-   Mount the microSD card and print the card type and size
-   Start Ethernet (DHCP) and request the time from an NTP server
-   Communicate with the GSM modem using AT commands
-   Transmit text over RS-485
-   Read the status of INPUT 1 to INPUT 4
-   Read the four analog input channels through the ADS1115

The program runs the following checks once at start-up, in this order:

-   Wi-Fi access point
-   RTC
-   microSD card
-   Ethernet and NTP
-   GSM modem (`AT`, `AT+CPIN?`, `AT+CSQ`, `AT+GSN`)

The program then continuously:

-   Prints the state of INPUT 1 to INPUT 4
-   Reads and prints the current value from analog input channels 0 to 3
-   Sends `RS485 01 SUCCESS` over RS-485
-   Passes anything typed in the Serial Monitor to the GSM modem and
    prints the modem reply
-   Prints data received through the serial interfaces

All results are shown on the Serial Monitor.

Follow the steps below to run the example.

### 1. Hardware Connections

-   Power the controller with the required DC supply.
-   Connect the USB cable to your computer.
-   Insert a microSD card (optional, for the SD test).
-   Connect an Ethernet cable (optional, for the Ethernet test).
-   Insert a SIM card and connect the GSM antenna (for the modem test).
-   Connect digital input signals to INPUT 1, INPUT 2, INPUT 3 and INPUT
    4.
-   Connect analog signals to analog input channels 0, 1, 2 and 3.
-   For the RS-485 test, connect an RS-485 device or a suitable loopback
    to the RS-485 terminals.
-   Ensure all input signals are within the supported electrical ranges
    specified in the product datasheet.

### 2. Configure the Program

No additional user configuration is required for this example before
upload.

### 3. Upload the Program

-   Open the example program in Arduino IDE / PlatformIO.
-   Select the appropriate ESP32 board and the correct port.
-   Upload the program to the NORVI controller.

### 4. Observe the Serial Monitor

Open the Serial Monitor at **115200 baud**.

When the program runs successfully:

-   The Wi-Fi access point starts and the MAC address and AP IP address
    are printed.
-   The RTC date and time are printed.
-   The SD card is mounted and its type and size are printed.
-   Ethernet attempts to obtain an IP address and request the NTP time.
-   The GSM modem responds to the AT commands, subject to SIM and
    network availability.
-   The states of the four digital inputs are printed.
-   The readings from analog input channels 0 to 3 are printed.
-   RS-485 test data is transmitted.

Example Output:

``` text
MAC Address: XX:XX:XX:XX:XX:XX
Setting up the Wi-Fi Access Point...
Access Point IP address: 192.168.4.1
Wi-Fi Access Point is active!

2026/10/27 Tuesday
Card Mount: success
Card Type: SDHC

AT
OK
+CPIN: READY
OK

1111
Current 0: 4.00 mA
Current 1: 8.00 mA
Current 2: 12.00 mA
Current 3: 16.00 mA

RS485 01 SUCCESS
----------------------
```

*Sample values only. The four digits show the states of INPUT 1 to INPUT
4. Analog readings depend on the connected signals.*

### How to Validate the Example

To verify the example works correctly:

1.  Confirm the Wi-Fi access point appears on your phone or computer.
    The SSID is the device MAC address and the password is `12345678`.
2.  Confirm the RTC date and time are printed.
3.  Confirm the SD card is mounted and its card type and size are
    printed.
4.  Confirm Ethernet obtains an IP address and the NTP time is printed
    when the network and NTP server are available.
5.  Confirm the modem responds to `AT` and returns SIM status for
    `AT+CPIN?`.
6.  Apply a valid signal to each digital input and observe the
    corresponding printed state.
7.  Apply suitable signals to analog input channels 0 to 3 and confirm
    that the readings change accordingly.
8.  Connect an RS-485 device or suitable loopback and verify the
    transmitted test data.

## Device Preparation / Configuration

Before running the example, ensure:

-   The controller is powered correctly.
-   The required digital and analog input signals are connected.
-   The SIM card and antenna are installed for the GSM test.
-   The Ethernet cable, microSD card and RS-485 connections are
    installed if those tests are required.

## Required Libraries

Install the following libraries before compiling:

-   Wire
-   WiFi
-   SPI
-   FS
-   SD
-   Adafruit_GFX
-   Adafruit_SSD1306
-   Adafruit_ADS1X15
-   Ethernet
-   RTClib

Installation:

1.  Open Arduino IDE.
2.  Go to Library Manager.
3.  Search for and install the required libraries. `Wire`, `WiFi`,
    `SPI`, `FS` and `SD` are included with the ESP32 core.

## Limitations

- This example is provided for demonstration purposes 
- Additional calibration may be required for precise measurements 
- Performance may depend on sensor accuracy and environmental conditions

## Safety Notes

-   Do not exceed the supported digital or analog input ratings.
-   Ensure correct polarity and wiring for all field signals.
-   Ensure proper grounding.
-   Disconnect power before wiring or making changes to connections.
-   Incorrect wiring may damage the controller.


Test Date: 27/10/2026 
Verified By: Kaveesha

---

**Test Date:** 2026-10-06  
**Verified By:** Kaveesha

---

## Support

Documentation: 
https://norvi.io/docs  
For additional support or inquiries, contact the NORVI support team. 
Datasheet : https://norvi.io/docs/norvi-gsm-ae08-i-l-datasheet/ 

## License

This example is provided for development and educational purposes.
