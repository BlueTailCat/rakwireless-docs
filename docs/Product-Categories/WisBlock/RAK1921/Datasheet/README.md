---
rak_desc: Provides comprehensive information about your RAK1921 to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisblock/rak1921/RAK1921.png
tags:
  - datasheet
  - wisblock
  - RAK1921
next: false
prev: ../Overview/
---

# RAK1921 WisBlock OLED Display Datasheet

## Overview

### Description

The RAK1921 module, part of the WisBlock series, is one of the modules that belong to the accessory category. This module was designed to be part of a production-ready IoT solution in a modular way. As part of the accessory category, it is not mandatory to be part of the final solution, but for certain cases can provide competitive advantages and improves the usability of the final solution.

RAK1921 is an OLED display module with a 128×64 dot matrix. The main characteristics of this module are the following: high brightness, self-emission, high contrast ratio, slim/thin outline, wide viewing angle, wide temperature range, and low power consumption.


### Features

* **Module specifications**
    * 0.96&nbsp;in OLED display
    * 128x64 pixel resolution
    * Bright white color on black background
    * I2C interface
    * Driver IC: SSD1306
    * Slim/thin Outline
    * Wide Viewing Angle
    * Wide Temperature Range
    * Low Power Consumption
    * Chipset: Solomon Systech Limited SSD1306
    * Module size: 27.8 x 27.3&nbsp;mm

## Specifications



### Hardware

The hardware specification is categorized into four parts. It discusses the interfacing, pinouts, and its corresponding functions and diagrams. It also covers the electrical and mechanical parameters that include the tabular data of the functionalities and standard values of the RAK1921 WisBlock OLED Display.

####  Chipset
| Vendor                  | Part number |
| ----------------------- | ----------- |
| Solomon Systech Limited | SSD1306     |


#### Interfaces

The RAK1921 module is compatible with the RAK5005-O WisBoard baseboard. The RAK5005-O has reserved a dedicated I2C port with a 2.54&nbsp;mm header, as shown in the red rectangle in **Figure 1**, in which the RAK1921 can be attached.

<rk-img
  src="/assets/images/wisblock/rak1921/datasheet/interface.png"
  width="30%"
  caption="I2C pin header in the RAK5005-O"
/>



:::tip 📝 NOTE:
Be careful in selecting the baseboard, and make sure to choose RAK5005-O because the RAK5005 is not compatible with the RAK1921 WisBlock OLED Display.
:::

#### Pin Definition

**Figure 2** shows the name of the pins available in the RAK1921 module. This module supports an I2C interface.

<rk-img
  src="/assets/images/wisblock/rak1921/datasheet/RAK1921-pin-definition.png"
  width="40%"
  caption="RAK1921 Pin Definition"
/>


| **Name** | **Description**                |
| -------- | ------------------------------ |
| VCC      | Power Supply (2.4 –3.5&nbsp;V) |
| GND      | Grounding                      |
| SCL      | I2C Clock Signal               |
| SDA      | I2C Data Signal                |


#### Electrical Characteristics

The absolute minimum and maximum ratings of the RAK1921 WisBlock OLED Display are presented in tabular representation. This should be followed accordingly to avoid future damages.

##### Absolute Maximum Ratings

| **Symbol**  | **Description**             | **Minimum** | **Nominal** | **Maximum** | **Unit** |
| ----------- | --------------------------- | ----------- | ----------- | ----------- | -------- |
| Vdd         | Power Supply for the Module | –0.5        |             | 3.5         | V        |
| Temperature | Operation Temperature       | –30         |             | 70          | ° C      |


##### Operating Conditions

| **Symbol** | **Description**        | **Minimum** | **Nominal** | **Maximum** | **Unit**   |
| ---------- | ---------------------- | ----------- | ----------- | ----------- | ---------- |
| Vdd        | Power Supply           | 2.4         |             | 3.5         | V          |
| Lbr        | Normal Mode Brightness | 80          | 100         |             | Cd/m²      |
|            | View Angle             | 160         |             |             | degree (°) |

#### Mechanical Characteristics

##### Board Dimensions

<rk-img
  src="/assets/images/wisblock/rak1921/datasheet/mechanical-dimensions.png"
  width="50%"
  caption="Mechanical Dimensions"
/>


