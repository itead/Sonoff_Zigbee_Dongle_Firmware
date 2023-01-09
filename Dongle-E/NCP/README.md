
[TOC]


# Dongle-E Zigbee NCP Firmware

This Zigbee NCP firmware is only tested on the EFR32MG21 based "Zigbee 3.0 USB Dongle Plus V2 model "ZBDongle-E" hardware from ITead.

* https://itead.cc/product/zigbee-3-0-usb-dongle/


## EmberZNet Zigbee NCP Configuration Parameter values table

Configuration Parameter | Value
-- | --
EMBER_APS_UNICAST_MESSAGE_COUNT | 32
EMBER_PACKET_BUFFER_COUNT | 250
EMBER_NEIGHBOR_TABLE_SIZE | 26
EMBER_SOURCE_ROUTE_TABLE_SIZE | 200
EMBER_ADDRESS_TABLE_SIZE | 32

## Changelog


#### 6.10.3 V1.0.1

Filename: "ncp-uart-sw_EZNet6.10.3_V1.0.1.gbl"

* 6.10.3.0 build 297

Notable changes for this release:
  * Initial release.
  * Based on Zigbee EmberZNet SDK 6.10.3.0 GA from Silicon Labs
  * Built with Silicon Labs Gecko SDK Suite 3.2
  * No Touchlink support
