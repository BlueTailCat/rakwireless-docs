---
rak_desc: Provides comprehensive information about your RAK12012 to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisblock/rak12012/RAK12012.png
tags:
  - datasheet
  - wisblock
  - RAK12012
prev: ../Quickstart/
next: false
---

# RAK12012 WisBlock Heart Rate Sensor Module Datasheet

## Overview

### Description

The RAK12012, a part of WisBlock Sensor, is an integrated pulse oximetry and heart-rate monitor module used for measuring person's heart rate and oxygen saturation. The sensor attached to this module is MAX30102 from Analog Devices.


### Features

- Heart-Rate Monitor and Pulse Oximeter Sensor in LED Reflective Solution
- Ultra-Low Power Operation
- Robust Motion Artifact Resilience
- Fast Data Output Capability
- -40&nbsp;°C to +85&nbsp;°C Operating Temperature Range
- 3.3&nbsp;V Power supply
- Operating Current: 0.7 - 1200&nbsp;uA
- Chipset: Analog Devices MAX30102
- Module Size: 25&nbsp;mm x 35&nbsp;mm

## Specifications

### Overview

#### Mounting

The RAK12012 WisBlock Heart Rate Sensor Module can be mounted to the IO slot of the [WisBlock Base](https://docs.rakwireless.com/Product-Categories/WisBlock/#wisblock-base) board. **Figure 1** shows the mounting mechanism of the RAK12012 on a WisBlock Base module.

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/mounting.png"
  width="60%"
  caption="RAK12012 WisBlock Heart Rate Sensor Module Mounting"
/>

With the [RAK19008 FPC Cable](https://store.rakwireless.com/)，RAK12012 can separated from the WisBlock Base board. The two (2) slots of the board are for the rubber bands. The rubber bands can help to press the sensor against the finger or wrist.

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/rak12012-labels.svg"
  width="70%"
  caption="RAK12012 WisBlock Heart Rate Sensor Module Mounting With Rubber Band"
/>


### Hardware

The hardware specification is categorized into five parts. It shows the chipset of the module and discusses the pinouts and its corresponding functions and diagrams. It also covers the electrical and mechanical parameters that include the tabular data of the functionalities and standard values of the RAK12012 WisBlock Heart Rate Sensor Module.

#### Chipset

| Vendor           | Part number |
| ---------------- | ----------- |
| Analog Devices | MAX30102    |


#### Pin Definition

The RAK12012 WisBlock Heart Rate Sensor comprises a standard WisBlock connector. The WisBlock connector allows the RAK12012 module to be mounted to a WisBlock Base board. The pin order of the connector and the pinout definition is shown in **Figure 3**.

::: tip 📝 NOTE
- **I2C** related pins: **INT**,**3V3_S**, and **GND** are connected to WisIO connector.
- **3V3_S** voltage output from the WisBlock Base that powers the RAK12012 module can be controlled by the WisBlock Core via WB_IO2 (WisBlock IO2 pin). This makes the module ideal for low-power IoT projects since the WisBlock Core can totally disconnect the power of the RAK12012 module.
:::

 <rk-img
  src="/assets/images/wisblock/rak12012/datasheet/rak12012_pinout.svg"
  width="80%"
  caption="RAK12012 WisBlock Heart Rate Sensor Module Pinout"
/>


#### Electrical Characteristics

##### Absolute Maximum Ratings

| Parameter                    | Minimum | Maximum | Unit |
| ---------------------------- | ------- | ------- | ---- |
| 3V3_S                        | -0.3    | 6       | V    |
| 1V8                          | -0.3    | 2.2     | V    |
| ESD (HBM)                    | -       | 2.5     | KV   |
| Operating Temperature Range  | -40     | 85      | °C   |
| Continuous Power Dissipation | -       | 440     | mW   |


##### Power Supply Ratings

| Symbol | Description                | Condition                                       | Min. | Nom. | Max. | Unit |
| ------ | -------------------------- | ----------------------------------------------- | ---- | ---- | ---- | ---- |
| 3V3_S  | LED Supply Voltage         | Input voltage must within this range            | 3.1  | 3.3  | 5    | V    |
| 1V8    | Analog Supply Voltage      | Input voltage must within this range            | 1.7  | 1.8  | 2    | V    |
| IDD1   | Supply Current             | SpO2 and HR mode，PW = 215&nbsp;µs，50&nbsp;sps | -    | 600  | 1200 | uA   |
| IDD2   | Supply Curren              | IR only mode, PW = 215&nbsp;µS, 50&nbsp;sps     | -    | 600  | 1200 | uA   |
| ISHDN  | Supply Current in Shutdown | TA = +25&nbsp;°C, MODE = 0x80                   | -    | 0.7  | 10   | uA   |


#### Mechanical Characteristics

##### Board Dimensions

**Figure 4** shows the dimensions and the mechanical drawing of the RAK12012 module.

 <rk-img
  src="/assets/images/wisblock/rak12012/datasheet/rak12012-dimension.svg"
  width="60%"
  caption="RAK12012 WisBlock Heart Rate Sensor Module Dimensions"
/>


##### WisConnector PCB Layout

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/pcb_footprint.png"
  width="100%"
  caption="WisConnector PCB Footprint and Recommendations"
/>


#### Schematic Diagram

##### Power Supply

**Figure 6** shows the MAX30102 power supply. The IC uses 1.8&nbsp;V as voltage supply source generated by SGM2019-1.8YN5G/TR (LDO). The VLED+ has a different dedicated power supply coming from the 3V3_S of the WisBlock Base board.

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/power_supply.png"
  width="80%"
  caption="RAK12012 WisBlock Heart Rate Sensor Module Power Supply"
/>


##### Voltage Level Transfer

The MAX30102 IO voltage is 1.8&nbsp;V and the CPU module voltage is 3.3&nbsp;V, so the voltage level transfer is needed. Pull-up Resistor for I2C_SCL and I2C_SDA already exist on WisBlock Base board，so there is no need to connect（NC）on IO module such as RAK12012.

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/voltage_level.png"
  width="50%"
  caption="The Voltage Level Transfer Circuit"
/>


##### MAX30105EFD+T Circuit

INT is an active-low interrupt (Open-Drain). This needs to be connected to an external voltage with a pull-up resistor **R7**.

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/MAX30105.png"
  width="50%"
  caption="MAX30105EFD+T Circuit"
/>

##### WisConnector

<rk-img
  src="/assets/images/wisblock/rak12012/datasheet/wisconnector.png"
  width="40%"
  caption="RAK12012 Module WisConnector"
/>

::: tip 📝 NOTE
- The **I2C** related pins: **INT **,**3V3_S**, and **GND** are connected to WisIO connector.
- The **3V3_S** supply can be disconnected to save power via **WB_IO2**.
:::
​


