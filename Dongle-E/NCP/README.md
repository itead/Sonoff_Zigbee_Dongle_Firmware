
[TOC]


# Dongle-E Zigbee NCP Firmware

Silicon Labs EmberZNet NCP Zigbee Coordinator firmware with Silicon Labs standard EZSP (EmberZNet Serial Protocol) interface.

This Zigbee NCP firmware has only been tested on the EFR32MG21 based "Zigbee 3.0 USB Dongle Plus V2 model "ZBDongle-E" hardware from ITead.

* https://itead.cc/product/zigbee-3-0-usb-dongle/

## Recommended firmware
At the time of writting (2022-06-30) EmberZNet Zigbee version 6.10.3.0 firmware is recommended for the ZHA integration in Home Assistant (which depends on the open source zigpy and bellows libraries):

* ncp-uart-sw_EZNet6.10.3_V1.0.1.gbl

The same firmware version has also been confirmed to work with OpenHAB Zigbee Binding, Zigbee2MQTT, IoBroker, Zigbee Plugin for Domoticz, and Zigbee Plugin for Jeedom.

## EmberZNet Zigbee NCP Configuration Parameter values table

Configuration Parameter | Value
-- | --
EMBER_APS_UNICAST_MESSAGE_COUNT | 32
EMBER_PACKET_BUFFER_COUNT | 250
EMBER_NEIGHBOR_TABLE_SIZE | 26
EMBER_SOURCE_ROUTE_TABLE_SIZE | 200
EMBER_ADDRESS_TABLE_SIZE | 32

More missing configuration?
* Child Table Size == ?
* CTUNE value == ?
* TX == PBxx?
* RX == PBxx?

## Versions and Changelog


#### 6.10.3 V1.0.1

Filename: "ncp-uart-sw_EZNet6.10.3_V1.0.1.gbl"

* 6.10.3.0 build 297

Notable changes for this release:
  * Initial release.
  * Based on Zigbee EmberZNet SDK 6.10.3.0 GA from Silicon Labs
  * Built with Silicon Labs Gecko SDK Suite 3.2
  * No Touchlink support

## Abbreviations diction legend:

Diction for commonly used shorthand and acronyms used in firmware image file names for Silabs based adapters:

* ncp = NCP (Network Co-Processor) design
* rcp = RCP (Radio Co-Processor) design
* s2 = EFR32 Series 2 (eg. EFR32MG2x such as EFR32MG21)
* s1 = EFR32 Series 1 (eg. EFR32MG1x)
* F1024 = 1024k Flash Size
* F512 = 512k Flash Size
* F256 = 256k Flash Size
* com = Combined (necessary for EFR32 Series 1)
* uart = UART interface
* nsw = no flow control
* sw = software flow control (XON/XOFF flow control)
* hw = hardware flow control (RTS/CTS flow control)
* 655 / 678 / 679 = EmberZNet Version which also indoicate version for EZSP (EmberZNet Serial Protocol)
* 115200 = Baud rate speed set to 115200
* 57600 = Baud rate speed set to 57600
* std = Standalone
* btl = Bootloader
* pb0-pb1 = Port used for TXD (Transceive Data) and RXD (Receive Data)
* pa0 = Bootloader GPIO Activation

## Firmware upgrade and recovery procedure

https://sonoff.tech/product-document/gateway-and-sensors-doc/zigbee-dongle-plus-efr32mg21-doc/

## Configurations used when compiling your own firmware with Silabs Simplicity Studio and EmberZNet Zigbee Stack

https://github.com/SiliconLabs/gecko_sdk

#### EmberZNet NCP Zigbee application firmware

EFR32MG21 target
NCP UART TX --> ?
NCP UART RC <-- ?
EZSP Version 8
DCDC

Configuration Parameter | Value
----------------------- | ------
Address Table Size | ?
Child Table Size | ?
Source Routes | ?
CTUNE value | ?

The remaining parameters are at the default values.

#### Gecko Bootloader firmware

EFR32MG21 target
Standalone Bootloader
NCP UART TX --> PA0
NCP UART RC <-- PA1
PB00/UART_BUTTON_RESET is bootloader activiation pin/button
Version: x.xx.x
DCDC

Use "1. upload gbl" and "xmodem(128 byte)" to send bootloader ota file to device.

## EFR32, EmberZNet and EZSP Protocol Versions

EZSP stands for "EmberZNet Serial Protocol" which is the default serial interface used in compatible Zigbee coordinator firmware for the Silicon Labs EFR32 hardware family such as the EFR32MG21/MGM210 and EFR32MG12/MGM12 series.

- https://www.silabs.com/wireless/zigbee/efr32mg21-series-2-socs
- https://www.silabs.com/wireless/zigbee/efr32mg21-series-2-modules

Silicon Labs do not currently have a consolidated list of changes by EmberZNet SDK or EZSP protocol versions. The EZSP additions, changes and deletions have only ever been listed in the [Zigbee EmberZNet Release Notes](https://www.silabs.com/search#q=Zigbee%20EmberZNet%20Release%20Notes&t=All&sort=relevancy) (EmberZNet SDK) under the "New items" section as well as the matching UG100 EZSP Reference Guide included with each EmberZNet SDK release.

The largest change was between EZSP v4 (first added in EmberZNet 4.7.2 SDK) and EZSP v5 that was added in EmberZNet 5.9.0 SDK which requires the Legacy Frame ID 0xFF. The change from EZSP v5 to EZSP v6 was done in EmberZNet 6.0.0 SDK. The change from EZSP v6 to EZSP v7 was in EmberZNet 6.4.0 SDK. EmberZNet 6.7.0 SDK added EZSP v8 (and Secure EZSP Protocol Version 2).

Perhaps more important to know is that EZSP v5, v6 and v7 (EmberZNet 6.6.x.x) use the same framing format, but EmberZNet 6.7.x.x/EZSP v8 introduced new framing format and expanded command id field from 8 bits to 16 bits.

See Silabs [Zigbee & Thread Knowledge Base Articles List](https://silabs-prod.adobecqms.net/community/wireless/zigbee-and-thread/knowledge-base.entry.html/2020/04/01/zigbee_thread_knowledgebasearticleslist-ih5r) for background information.
