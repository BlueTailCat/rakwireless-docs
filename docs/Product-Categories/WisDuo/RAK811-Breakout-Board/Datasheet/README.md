---
rak_desc: Provides comprehensive information about your RAK811 Breakout Board to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisduo/rak811-breakout-board/RAK811-Breakout.png
tags:
  - datasheet
  - wisduo
  - RAK811 Breakout Board
prev: ../Quickstart/
next: ../AT-Command-Manual/
certifications:
  - [CE, https://downloads.rakwireless.com/LoRa/RAK811/Certification_Report/RAK811_CE_Certification.zip]
  - [FCC, https://downloads.rakwireless.com/LoRa/RAK811/Certification_Report/RAK811_FCC_Certification.zip]
  - [KCC, https://downloads.rakwireless.com/LoRa/RAK811/Certification_Report/RAK811_KC_Certification.pdf]
  - [MIC, https://downloads.rakwireless.com/LoRa/RAK811/Certification_Report/RAK811_MIC_Certification.zip]
  - [RoHS, https://downloads.rakwireless.com/LoRa/RAK811/Certification_Report/RAK811_RoHS_Certification.zip]


---

# RAK811 Breakout Board Datasheet



## Overview

### Description

**RAK811 Breakout Board** is an easy-to-use, compact, and low-power long-range LoRa technology with wireless transceiver capabilities. It is based on RAK811 Stamp Module attached to a breakout board on Xbee form factor with standard 2.00&nbsp;mm headers.

The RAK811 Breakout Board complies with Class A & C of LoRaWAN 1.0.2 specification. Additionally, it supports LoRa Point-to-Point (P2P) communications, which help you in implementing their own private LoRa wireless applications. You can configure the mode and operation of the module using AT commands via the UART interface. RAK811 board also offers low-power features, which are very suitable for battery-powered applications.

### Features

- Based on **Semtech SX1276**.
- **LoRaWAN 1.0.2** specification compliant.
- **Supported bands**: EU433, CN470, IN865, EU868, AU915, US915, KR920, and AS923.
- LoRaWAN Activation by OTAA/ABP.
- LoRa Point-to-Point (P2P) communication.
- Integrates both **SMA** and **iPEX** antenna connectors.
- Xbee form factor with standard 2.00&nbsp;mm headers.
- Easy to use AT Command Set via UART interface with configurable baud rate.
- Maximum output power 100&nbsp;mW (20&nbsp;dBm), adjustable from 5 to 20&nbsp;dBm.
- High sensitivity at -148&nbsp;dBm, enabling extremely long range connectivity.
- Long-range - greater than 15&nbsp;km with optimized antenna.
- Low power consumption: 11&nbsp;μA on on standby.
- Ultra-Low Power Consumption of 11.9&nbsp;μA (down to 1.11&nbsp;μA @ 2.1&nbsp;V) in sleep mode.
- Multi-channel, dual data buffer (256&nbsp;bytes each).
- LoRa/FSK/GFSK/OOK modulation, bidirectional two-way communication.
- Long battery life for battery-powered applications.
- LoRa technology is capable of demodulating 20&nbsp;dB below noise level which significantly improves immunity to interference when combined with integrated forward error correction.
- **Operating temperature**: -30°&nbsp;C ~ 85°&nbsp;C (industrial grade)
- **Storage temperature**: -40°&nbsp;C ~ 85°&nbsp;C (non-condensing)

## Specifications

This section covers the hardware and software specifications of the RAK811 Breakout Board. All discussion presents both versions: RAK811(L) and RAK811(H).

### Overview

The **RAK811 Breakout Board** is shown in **Figure 1** with its corresponding board dimension of **42&nbsp;mm x 25&nbsp;mm**. This board weighs at about **0.2&nbsp;kg**.

<rk-img
  src="/assets/images/wisduo/rak811-breakout-board/datasheet/2.dimensions.svg"
  width="45%"
  caption="RAK811 Breakout Board Dimensions"
/>

### Hardware

The hardware specification is categorized into six parts. It discusses the pinouts of the board and its corresponding functions and diagrams. It also covers the RF, electrical, environmental, and mechanical parameters that include the tabular data of the functionalities and standard values of the RAK811 Breakout Board.

#### Interfaces

| Module                | Interfaces   |
| --------------------- | ------------ |
| RAK811 Breakout Board | UART1, GPIOs |

#### Pin Definition

The RAK811 Breakout Board supports two different frequency variations: **Low Radio Frequency** and **High Radio frequency**.

##### 1. Low Radio Frequency (RAK811(L))

The low radio frequency is applicable to the bandwidth of regions EU433 and CN470. For more information, refer to the [RF Characteristics](#rf-characteristics).

###### Low RF Pin Outline

<rk-img
  src="/assets/images/wisduo/rak811-breakout-board/datasheet/3.board-pinout-for-rak811-low-rf.png"
  width="50%"
  caption="Board Pinout for RAK811 Breakout Low RF"
/>

###### Low RF Pin Definition

| **Pin No.** | **Name**       | **Type** | **Description**                             |
| ----------- | -------------- | -------- | ------------------------------------------- |
| 1           | VCC 3.3&nbsp;V | P        | Main Power Voltage Source Input             |
| 2           | PA9/UART1_TX   | O        | UART1 Interface (AT Commands and FW Update) |
| 3           | PA10/UART1_RX  | I        | UART1 Interface (AT Commands and FW Update) |
| 4           | PB12/ADC       | I/O      | GPIO and ADC                                |
| 5           | RST            | I        | Reset Trigger Input, Low Active             |
| 6           | PA3/ADC        | I/O      | GPIO and ADC                                |
| 7           | PB5            | I/O      | GPIO only                                   |
| 8           | PA12           | I/O      | GPIO only                                   |
| 9           | PB4            |          | Boot mode GPIO enable pin - high active     |
| 10          | GND            |          | Ground connections                          |
| 11          | PA0/ADC        | I/O      | GPIO and ADC                                |
| 12          | PA1/ADC        | I/O      | GPIO and ADC                                |
| 13          | PA14           |          | SWD Debug Pin (SWCLK)                       |
| 14          | PA13           |          | SWD Debug Pin SWDIO                         |
| 15          | PA11           | I/O      | GPIO only                                   |
| 16          | PB15/ADC       | I/O      | GPIO and ADC                                |
| 17          | PA2/ADC        | I/O      | GPIO and ADC                                |
| 18          | PB13/ADC       | I/O      | GPIO and ADC                                |
| 19          | PA12/ADC       | I/O      | GPIO and ADC                                |
| 20          | PB14/ADC       | I/O      | GPIO and ADC                                |

##### 2. High Radio Frequency (RAK811(H))

The high radio frequency hardware supports the regions of EU868, US915, AU915, KR920, AS923, and IN865. For more information, refer to the [RF Characteristics](#rf-characteristics).

###### High RF Pin Outline

<rk-img
  src="/assets/images/wisduo/rak811-breakout-board/datasheet/4.board-pinout-for-rak811-high-rf.png"
  width="50%"
  caption="Board Pinout for RAK811 Breakout High RF"
/>

###### High RF Pin Definition

| **Pin No.** | **Name**       | **Type** | **Description**                             |
| ----------- | -------------- | -------- | ------------------------------------------- |
| 1           | VCC 3.3&nbsp;V | P        | Main Power Voltage Source Input             |
| 2           | PA9/UART1_TX   | O        | UART1 Interface (AT Commands and FW Update) |
| 3           | PA10/UART1_RX  | I        | UART1 Interface (AT Commands and FW Update) |
| 4           | PB12/ADC       | I/O      | GPIO and ADC                                |
| 5           | RST            | I        | Reset Trigger Input, Low Active             |
| 6           | PB3            | I/O      | GPIO only                                   |
| 7           | PB5            | I/O      | GPIO only                                   |
| 8           | PA15           | I/O      | GPIO only                                   |
| 9           | BOOT0          |          | Boot mode GPIO enable pin - high active     |
| 10          | GND            |          | Ground connections                          |
| 11          | PA0/ADC        | I/O      | GPIO and ADC                                |
| 12          | PA1/ADC        | I/O      | GPIO and ADC                                |
| 13          | PA14           |          | SWD Debug Pin (SWCLK)                       |
| 14          | PA13           |          | SWD Debug Pin (SWDIO)                       |
| 15          | PB4            | I/O      | GPIO only                                   |
| 16          | PB15/ADC       | I/O      | GPIO and ADC                                |
| 17          | PA2/ADC        | I/O      | GPIO and ADC                                |
| 18          | PA8            | I/O      | GPIO only                                   |
| 19          | PA12           | I/O      | GPIO only                                   |
| 20          | PB14/ADC       | I/O      | GPIO and ADC                                |


#### RF Characteristics

##### Operating Frequencies

| Module    | Region        | Frequency |
| --------- | ------------- | --------- |
| RAK811(L) | Europe        | EU433     |
|           | China         | CN470     |
| RAK811(H) | Europe        | EU868     |
|           | North America | US915     |
|           | Australia     | AU915     |
|           | Korea         | KR920     |
|           | Asia          | AS923     |
|           | India         | IN865     |

| Feature        | Condition | Minimum | Typical | Maximum | Unit |
| -------------- | --------- | ------- | ------- | ------- | ---- |
| Transmit       | TX Power  |         | 14      | 20      | dBm  |
| RX Sensitivity | RSSI      | -130    |         |         | dBm  |
|                | SNR       | -15     |         |         | dB   |

#### Electrical Characteristics

##### Schematic Diagram


<rk-img
  src="/assets/images/wisduo/rak811-breakout-board/datasheet/5.schematic-diagram-for-rak811.jpg"
  width="100%"
  caption="RAK811 Schematic Diagram"
/>


<rk-img
  src="/assets/images/wisduo/rak811-breakout-board/datasheet/6.reference-design.png"
  width="100%"
  caption="Reference Design"
/>

##### Operating Voltage

| Feature | Minimum | Typical | Maximum | Unit      |
| ------- | ------- | ------- | ------- | --------- |
| VCC     | 2.1     | 3.3     | 3.45    | Volts (V) |

##### Current Consumption

| Feature             | Condition | Minimum                 | Typical | Maximum | Unit |
| ------------------- | --------- | ----------------------- | ------- | ------- | ---- |
| Current Consumption | TX Power  | 30 (@&nbsp;14&nbsp;dBm) |         |         | mA   |
|                     | RX Mode   | 5.5                     |         |         | mA   |

##### Sleep Current

| Feature             | Condition | Minimum (2.1V) | Typical (3.3V) | Maximum | Unit |
| ------------------- | --------- | -------------- | -------------- | ------- | ---- |
| Current Consumption | EU868     | 8.37           | 11.9           |         | μA   |
|                     | US915     | 1.11           | 11.8           |         | μA   |
|                     | CN470     | 1.65           | 3.07           |         | μA   |

#### Mechanical Characteristics

##### Module Dimensions

<rk-img
  src="/assets/images/wisduo/rak811-breakout-board/datasheet/7.rak811-physical-dimension.jpg"
  width="55%"
  caption="RAK811 Physical Dimension"
/>



#### Environmental Characteristics

##### Operating Temperature

| Feature               | Minimum | Typical | Maximum | Unit |
| --------------------- | ------- | ------- | ------- | ---- |
| Operating Temperature | -30     | 25      | 85      | °C   |

##### Storage Temperature

| Feature             | Minimum | Typical | Maximum | Unit |
| ------------------- | ------- | ------- | ------- | ---- |
| Storage Temperature | -40     |         | 85      | °C   |


### Software

Download the latest firmware of the RAK811 Breakout Board — both in low and high frequency — provided in the table below.

:::tip 📝 NOTE:

The **bin file** contains the application code only, and you need the RAK DFU Tool to upload this file to the module.

The **hex file** contains both the bootloader and the application code. You need to use STM32CubeProgrammer to upload this.

:::

#### Firmware / OS

| Model     | Version     | Source                                                                                                        |
| --------- | ----------- | ------------------------------------------------------------------------------------------------------------- |
| RAK811(L) | V3.0.0.14.L | [Download](https://downloads.rakwireless.com/LoRa/RAK811-BreakoutBoard/Firmware/RAK811_L_Latest_Firmware.zip) |
| RAK811(H) | V3.0.0.14.H | [Download](https://downloads.rakwireless.com/LoRa/RAK811-BreakoutBoard/Firmware/RAK811_H_Latest_Firmware.zip) |

## Certification

<rk-certifications :params="$page.frontmatter.certifications" />