---
rak_desc: Provides comprehensive information about your RAK5860 to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisblock/rak5860/RAK5860.png
prev: ../Quickstart/
next: false
tags:
  - Datasheet
  - WisBlock
  - RAK5860
certifications:
  - [CE, https://downloads.rakwireless.com/LoRa/WisBlock/RAK5860/Certification/RAK5860_CE_Certification.zip]
  - [FCC, https://downloads.rakwireless.com/LoRa/WisBlock/RAK5860/Certification/RAK5860_FCC_Certification.pdf]

---

# RAK5860 WisBlock NB-IoT Interface Module Datasheet

## Overview

### Description

The RAK5860 WisBlock Connect module is designed to be part of a production-ready IoT solution in a modular way and must be combined with a WisBlock Core and a Base module.

The RAK5860 is a module designed to work with the RAK5005-O baseboard and it provides wireless communication (LTE Cat M1, LTE Cat NB2) to the final application. This module supports the LTE-FDD network and supports half-duplex operation in the LTE network. It also provides optional GNSS functionality.

For debugging purposes, a Micro-USB connector is used for sending AT commands, data transmission, and receiving GNSS NMEA output. Once the module is integrated with the RAK5005-O baseboard, the internal UART port of the module is connected through the IO connector to a WisBlock Core module.

### Features

* Quectel BG77 with LTE Cat M1, LTE cat NB2, and GNSS
* IPEX connectors for the LTE and GPS antenna
* Micro-USB connector
* Nano SIM and ESIM options
* Status Indication LEDs
* Power Supply: 2.6-4.2&nbsp;V, typical supply voltage 3.3&nbsp;V
* Module size: 25&nbsp;mm x 35&nbsp;mm

## Specifications

### Overview

The overview shows the realistic view of the RAK5860 module and its block diagram. It also covers the installation mechanism of the module into the baseboard.

#### Board Overview

**Figure 1** shows a realistic view and main component description of the RAK5860 Module.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/board-overview-1.png"
  width="50%"
  caption="RAK5860 Board Realistic View (Front)"
/>


<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/board-overview-2.png"
  width="50%"
  caption="RAK5860 Board Realistic View (Back)"
/>

#### Mounting Sketch

**Figure 3** shows how the RAK5860 module (a WisIO module) is integrated with the RAK5005 baseboard. The mounting sketch is also shown.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/mounting-sketch.png"
  width="60%"
  caption="Mounting Sketch"
/>

#### Block Diagram

<br>

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/block-diagram.svg"
  width="50%"
  caption="RAK5860 Block Diagram"
/>

### Hardware

The hardware specification of the RAK5860 is categorized into two. It covers the electrical standard ratings and the functionalities of the module. It also discusses the diagram of the module and its mechanism.

#### Chipset
| Vendor  | Part number |
| ------- | ----------- |
| Quectel | BG77        |


#### Electrical Characteristics

##### Absolute Maximum Ratings

The table below shows the absolute maximum ratings of the RAK5860 module.

| **Symbol**              | **Description**             | **Min.** | **Nom.** | **Max.** | **Unit** |
| ----------------------- | --------------------------- | -------- | -------- | -------- | -------- |
| VBAT                    | Power Supply for the Module | -0.5     | -        | 4.2      | V        |
| USB_VBUS                | USB Connection Detection    | 1.3      | -        | 1.8      | V        |
| Voltage at Digital Pins | -                           | -0.3     | -        | 2.09     | V        |

##### Recommended Operating Conditions

The table below shows the recommended operating conditions of the RAK5860 module.

| **Symbol** | **Description**             | **Min.** | **Nom.** | **Max.** | **Unit** |
| ---------- | --------------------------- | -------- | -------- | -------- | -------- |
| VBAT       | Power Supply for the Module | 2.6      | 3.3      | 4.2      | V        |
| USB_VBUS   | USB Connection Detection    | 1.3      | -        | 1.8      | V        |
| USBPHY_3P3 | Power for USB PHY Circuit   | -        | 3.3      | -        | V        |

:::warning ⚠️ WARNING
A battery connected to the WisBlock Base is required. USB power is not enough to make the module work reliably.
:::

#### Mechanical Characteristics

**Figure 5** shows the dimensions of the RAK5860 module.

##### Board Dimensions

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/mechanical_dimensions.png"
  width="30%"
  caption="Mechanical Dimensions"
/>

##### WisConnector PCB Layout

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/MxxS1003K6M.png"
  width="100%"
  caption="WisConnector PCB footprint and recommendations"
/>

#### Schematic Diagram

The following sections will describe the schematic of the RAK5860 module, which include:

* Turn on/off Module
* IO Connector
* Voltage-level Translator
* SIM Card Circuit
* USB Connector
* Status Indication LEDs
* Main Antenna
* GNSS Antenna

##### Turn On/Off Mechanism

**Figure 7** shows a circuit to allow the turn on or to turn off the module. By default, the internal Quectel BG77 module is in power-off mode, it can be turned on by driving WIS_PWRKEY to a high state (positive digital pulse) for a period of 500-1000&nbsp;ms.

Driving WIS_PWRKEY high for 650-1500&nbsp;ms, the module will execute a power-down procedure after WIS_PWRKEY is released, then enter off mode.

Alternatively, you can send a command **`AT+QPOWD`** command that turns off the internal Quectel BG77 module.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/turn-on-off.png"
  width="40%"
  caption="Turn On/Off Module Circuit"
/>

##### IO Connector

**Figure 8** shows the definition of the IO connector.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/wisio-connector.png"
  width="60%"
  caption="WisIO Connector Pin Definition"
/>

The RAK5860 only uses a subset of all the pins available in the IO connector. These are shown in the table below:

| **Name**   | **Description**                         | **Comment**                                                                                                                                                         |
| ---------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| VBAT       | BG77 Power Supply                       | Max 4.2&nbsp;V                                                                                                                                                      |
| 3v3_S      | 3.3&nbsp;V for GNSS Antenna             | 3V3_S is controlled by IO2 of WisBlock (P1.02 of NRF52840). This pin must be set HIGH in your code so that the active GPS antenna has a power supply and will work. |
| 3V3        | 3.3&nbsp;V For Voltage Level Transistor |                                                                                                                                                                     |
| WIS_PWRKEY | Turn on/off BG77                        | Active High                                                                                                                                                         |
| WIS_TX     | UART TXD                                | BG77 MAIN_RX, 1.8&nbsp;V power domain                                                                                                                               |
| WIS_RX     | UART RXD                                | BG77 MAIN_TX, 1.8&nbsp;V power domain                                                                                                                               |


##### IO Connector Pin Order

**Figure 9** shows the IO connector’s pin order. The connector is located in the bottom layer of the RAK5860 module.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/pin_order.png"
  width="40%"
  caption="IO Connector Pin Order"
/>

##### Voltage-level Translator

Within the BG77, all interfaces are designed to work with 1.8&nbsp;V level. RAK5860 features a voltage-level translator to down-convert the 3.3&nbsp;V coming from the WisBlock Core module. **Figure 10** shows the design of the internal voltage-level translator.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/voltage-level-translator.png"
  width="40%"
  caption="3.3 V to 1.8 V voltage-level translator"
/>

* When WIS_TX is high (3.3&nbsp;V), the NPN triode is turned off, BG77_RX is pulled high (1.8&nbsp;V).

* When WISTX is low (0&nbsp;V), the NPN triode is turned on, BG77 RX is low (0&nbsp;V).

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/voltage_level-translator-1.png"
  width="40%"
  caption="1.8 V to 3.3 V voltage-level translator"
/>

* When BG77_TX is low (0&nbsp;V), the NPN triode is turned on, WIS_RX is low (0&nbsp;V)

* When BG77TX is high (1.8&nbsp;V), the NPN triode is turned off, and WIS RX is pulled high (3.3&nbsp;V)

:::tip 📝 NOTE:
VDD_EXT is 1.8&nbsp;V, from BG77 internal regulator, BG77 pin 21.
:::

##### SIM Card Circuit

The RAK5860 module only supports the 1.8&nbsp;V ESIM/SIM card. **Figure 12** shows the SIM interface circuit. By default, a Nano SIM card is used, and eSIM is not mounting. To offer good ESD protection, a TVS diode array is added to the SIM card circuitry.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/sim-card.png"
  width="85%"
  caption="SIM Card Circuit"
/>

##### USB Connector

The RAK5860 module provides a Micro-USB connector for connection with a host device. The USB data lines USB+ and USB- are connected directly to the BG77. The VBUS line can be used for USB connection detection.

To offer good ESD protection, a TVS diode array is added to the USB connector circuit.


<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/usb_connector.png"
  width="40%"
  caption="USB Connector"
/>

The USB connection detection pin input voltage range is 1.3~1.8&nbsp;V. **Figure 14** shows the USB connection detection pin power supply.


<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/usb_connection_detection.png"
  width="30%"
  caption="USB connection detection pin power supply"
/>

##### Power Supply for USB PHY Circuit

**Figure 15** shows the power supply for the USB PHY circuit.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/usb_phy.png"
  width="50%"
  caption="Power supply for USB PHY circuit"
/>

##### Status Indication LEDs

**Figure 16** shows the operation status and network activity status. When BG77 is powered on, the blue led is lit. Different activity network status, the green led is lit or not is different.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/status_indication-led.png"
  width="60%"
  caption="Status indication LED circuit"
/>

##### Main Antenna

The RAK5860 module’s main antenna has a reserve π-type matching circuit for better RF performance, and a U.FL connector is used for the main antenna.

<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/main_antenna.png"
  width="30%"
  caption="Main Antenna Circuit"
/>

##### GNSS Antenna

The RAK5860 module is designed with an active antenna. The 3V3_S is from the WisIO connector, and a U.FL connector is used for the GNSS antenna. **Figure 18** shows the GNSS antenna circuit.

:::tip 📝 NOTE:
3V3_S is controlled by IO2 of WisBlock (P1.02 of NRF52840). For the active GPS antenna to work, set the pin to HIGH in your code.
:::


<rk-img
  src="/assets/images/wisblock/rak5860/datasheet/gnss_antenna.png"
  width="50%"
  caption="GNSS Antenna circuit"
/>

## Certification

<rk-certifications :params="$page.frontmatter.certifications" />
