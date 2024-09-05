---
rak_desc: Provides comprehensive information about your RAK7268V2 to help you use it. This information includes technical specifications, characteristics, and requirements, and it also discusses the device components.
rak_img: /assets/images/wisgate/rak7268-v2/RAK7268V2.png
tags:
  - datasheet
  - wisgate
  - RAK7268V2
  - RAK7268CV2
prev: ../Supported-LoRa-Network-Servers/
next: false
certifications:
  - [Anatel, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268V2_ANATEL_Certification.pdf]
  - [Anatel, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268CV2_ANATEL_Certification.pdf]
  - [CE, https://downloads.rakwireless.com/LoRa/RAK7268V2/Certification/RAK7268V2_CE_Certification.zip]
  - [FCC, https://downloads.rakwireless.com/LoRa/RAK7268V2H/Certification/RAK7268CV2H_RAK7268V2H_FCC_Certification.pdf]
  - [JRL, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268_RAK7268V2_RAK7268C_RAK7268CV2_JRL_Certification.pdf]
  - [JTBL, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268_RAK7268V2_JTBL_Certification.pdf]
  - [KCC, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268V2_RAK7268CV2_KC_Certification.pdf]
  - [RCM, https://downloads.rakwireless.com/LoRa/RAK7268V2H/Certification/RAK7268CV2H_RAK7268V2H_RCM_Certification.pdf]
  - [REACH, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268C_RAK7268CV2_RAK7268_RAK7268V2_REACH_Report.pdf]
  - [RoHS, https://downloads.rakwireless.com/LoRa/RAK7268/Certification/RAK7268C_RAK7268CV2_RAK7268_RAK7268V2_RoHS_Report.pdf]
  - [RSM, https://downloads.rakwireless.com/LoRa/RAK7268V2H/Certification/RAK7268CV2H_RAK7268V2H_RSM_Certification.pdf]
  - [UKCA, https://downloads.rakwireless.com/LoRa/RAK7268V2H/Certification/RAK7268CV2H_RAK7268V2H_UKCA_Certification.pdf]
---

# RAK7268V2/RAK7268CV2 WisGate Edge Lite 2 Datasheet

## Overview

### Description

The RAK7268V2 WisGate Edge Lite 2 is the latest edition of the RAK Edge Series. It is an ideal product for indoor deployment with its built-in Ethernet connectivity for a straightforward setup. Additionally, there is an onboard Wi-Fi setup (supporting 2.4&nbsp;GHz Wi-Fi) that allows it to be easily configured via the default Wi-Fi AP mode. The new RAK7268V2 supports power-over-Ethernet (PoE) in cases of a wall or ceiling mounting, where installing additional power lines is not an option. Moreover, the gateway supports LTE uplink communication connections (optional, only in RAK7268CV2).

The RAK7268V2 supports WisGateOS 2, which is based on the latest OpenWRT kernel and accommodates the latest security updates like IPv6, OpenSSL 1.1 support, multiple accounts access, and more. The web UI has a fresh new look, with more user-friendly information tooltips.

RAK7268V2 is especially suitable for small and medium-sized deployment scenarios in industry applications, saving the additional cost for server and R&D investment, and has the advantages of high execution efficiency.



### Features

- Full LoRaWAN Stack support (V 1.0.3) with Semtech SX1302
- Supports 2.4&nbsp;GHz Wi-Fi AP for configuration
- 100M Base-T Ethernet with PoE
- Multi back-haul with Ethernet, Wi-Fi, Cellular
- OpenWRT software supports Web UI for easy configuration and monitoring
- Can integrate with both private (ChirpStack) and public (TTN) network servers
- TF card for log backup and LoRa frame buffering (in case of backhaul failover)
- Built-in Network Server for easy deployment of applications and integration of gateways
- LTE Cat 4 network (optional)

:::tip 📝 NOTE:
A 9~24 VDC power input version of RAK7268V2 or RAK7268CV2 WisGate Edge Lite 2 is available upon request. For more information or to make a purchase, kindly contact [inquiry@rakwireless.com](mailto:inquiry@rakwireless.com).
:::

## Specifications


### Overview

The overview presents the block diagram for the RAK7268V2 that shows the internal architecture of the board.

#### Block Diagram


<rk-img
  src="/assets/images/wisgate/rak7268-v2/datasheet/block-diagram-without-lte.png"
  width="100%"
  caption="RAK7268V2 WisGate Edge Lite 2 without LTE Block Diagram"
/>


<rk-img
  src="/assets/images/wisgate/rak7268-v2/datasheet/block-diagram-with-lte.png"
  width="100%"
  caption="RAK7268CV2 WisGate Edge Lite 2 with LTE Block Diagram"
/>

### Main Specifications

<table>
    <thead>
      <tr><th>Feature</th><th>Specifications</th></tr>
    </thead>
    <tbody>
        <tr><td>Computing</td><td>MT7628, DDR2 RAM 128&nbsp;MB</td></tr>
        <tr><td rowspan="4">Wi-Fi Feature</td><td>Frequency: 2.4&nbsp;GHz (802.11b /g / n)</td></tr>
        <tr><td>RX Sensitivity:﹣95&nbsp;dBm (Min)</td></tr>
        <tr><td>TX Power: 20&nbsp;dBm (Max)</td></tr>
        <tr><td>Operation channels: 2.4&nbsp;GHz, 1-13</td></tr>
        <tr><td rowspan="5">LoRa Feature</td><td>SX1302 Mini PCIe card</td></tr>
        <tr><td>8 Channels</td></tr>
        <tr><td>RX Sensitivity:﹣139&nbsp;dBm (Min)</td></tr>
        <tr><td>TX Power: 27&nbsp;dBm (Max)</td></tr>
        <tr><td>Frequency: EU868 / IN865 / RU864 / US915 / AU915 / KR920 /AS923-1-2-3-4 / EU433 / CN470</td></tr>
        <tr><td rowspan="23">Cellular Feature (optional, available with RAK7268CV2)</td><td><b>Nano SIM Card:</b> 12.30 x 8.80 x 0.67&nbsp;mm<br>Supports Quectel EG95-E / EG95-NA / EC25-J / EC25-AU / EC25-E (IoT / M2M -optimized LTE Cat 4 Module)</td></tr>
        <tr><td><b>EG95-E for EMEA Region</b></td></tr>
        <tr><td>LTE FDD: B1 / B3 / B7 / B8 / B20 / B28A</td></tr>
        <tr><td>WCDMA: B1 / B8</td></tr>
        <tr><td>GSM/EDGE: B3 / B8</td></tr>
        <tr><td><b>EG95-NA for North America Region</b></td></tr>
        <tr><td>LTE FDD: B2 / B4 / B5 / B12 / B13</td></tr>
        <tr><td>WCDMA: B2 / B4 / B5</td></tr>
        <tr><td><b>EC25-J for Japan Region</b></td></tr>
        <tr><td>LTE FDD: B1 / B3 / B8 / B18 / B19 / B26</td></tr>
        <tr><td>LTE TDD: B41</td></tr>
        <tr><td>WCDMA: B1 / B6 / B8 /B19</td></tr>
        <tr><td><b>EC25-AU for Latin American/Australia/New Zealand Region</b></td></tr>
        <tr><td>LTE FDD: B1 / B2 / B3/ B4/ B5 / B7 / B8 /B28</td></tr>
        <tr><td>LTE TDD: B40</td></tr>
        <tr><td>WCDMA: B1 / B2 / B5 / B8</td></tr>
        <tr><td>GSM: B2 / B3 / B5 / B8</td></tr>
        <tr><td><b>EC25-E for Korea/India Region</b></td></tr>
        <tr><td>LTE FDD: B1 / B3 / B5 / B7 / B8 / B20</td></tr>
        <tr><td>LTE TDD: B38 / B40 / B41</td></tr>
        <tr><td>WCDMA: B1 / B5 / B8</td></tr>
        <tr><td>GSM: B3 / B8</td></tr>
        <tr><td><b>Optional supports other PCIe LTE module for Global Region</b></td></tr>
        <tr><td rowspan="3">Power Supply</td><td>DC 12&nbsp;V - 1&nbsp;A</td></tr>
        <tr><td>PoE (IEEE 802.3 af), 36~57&nbsp;VDC</td></tr>
        <tr><td>(Optional) 9~24&nbsp;VDC input upon request. Kindly contact <a href="mailto:inquiry@rakwireless.com">inquiry@rakwireless.com</a>. </td></tr>
        <tr><td>Power Consumption</td><td>12&nbsp;W (typical)</td></tr>
        <tr><td>ETH</td><td>RJ45 (10/100 M)</td></tr>
        <tr><td>Console</td><td>Type-C USB</td></tr>
        <tr><td rowspan="2">Antenna</td><td>LoRa: RP-SMA female connector</td></tr>
        <tr><td>Wi-Fi / LTE: Internal antenna</td></tr>
        <tr><td rowspan="6">LEDs</td><td>Power LED</td></tr>
        <tr><td>Breathing LED (Top side)</td></tr>
        <tr><td>ETH LED (On ETH connector)</td></tr>
        <tr><td>LoRa LED</td></tr>
        <tr><td>WLAN LED</td></tr>
        <tr><td>LTE LED (functional only in RAK7268CV2)</td></tr>
        <tr><td>Ingress Protection</td><td>IP30</td></tr>
        <tr><td>Enclosure Material</td><td>Plastic (PC+ABS)</td></tr>
        <tr><td>Weight</td><td>0.3 kg</td></tr>
        <tr><td>Dimensions</td><td>166 x 127.5 x 36&nbsp;mm Gateway only (no antenna, no bracket)</td></tr>
        <tr><td>Operating Conditions</td><td>Operating Temperature:﹣10&nbsp;˚C to﹢55&nbsp;˚C<br>Storage Temperature:﹣40&nbsp;˚C to﹢85&nbsp;˚C<br>Operating Humidity: 0~95&nbsp;% RH non-condensing<br>Storage Humidity: 0~95&nbsp;% RH non-condensing</td></tr>
        <tr><td>Installation Method</td><td>Desktop mounting<br>Wall mounting (via included bracket)<br>Rail mounting (via included bracket)</td></tr>
    </tbody>
</table>

### Hardware

The hardware specification covers the interfacing of the RAK7268V2 and its corresponding functionalities. It also presents the parameters and the standard values of the board.

#### Interfaces

The hardware interfaces of RAK7268V2 / RAK7268CV2 gateway include DC 12 V, ETH interface, Console interface, Reset key, SD Card slot, NanoSIM Card slot, Status indicator LEDs, LoRa Antenna connector, etc.

<rk-img
  src="/assets/images/wisgate/rak7268-v2/datasheet/interfaces.png"
  width="100%"
  caption="RAK7268V2 interfaces"
/>

:::tip 📝 NOTE

- Both RAK7268V2 and RAK7268CV2 have SIM slots, but only RAK7268CV2 has an integrated cellular module.

- The SD card found in the SD card slot must not be ejected, as it might affect the performance of the device, as different logs and data are stored on it.

:::

##### Reset Key Functions

The functions of the Reset key are as follows:

- **Short press**: Restart the gateway.
- **Long press** (5&nbsp;sec and above): Restore factory settings.

##### LED Indicators

<table>
    <thead>
        <tr><th>LEDs</th><th>Status Indication Description</th></tr>
    </thead>
    <tbody>
        <tr><td>PWR LED</td><td>Power indicator - The LED is on when device power is on</td></tr>
        <tr><td>Breathing LED</td><td>Indicates the current status of the gateway. The breathing light can be programmed </td></tr>
        <tr><td rowspan="3">ETH LED</td><td>ON - Linkup</td></tr>
        <tr><td>OFF - Linkdown</td></tr>
        <tr><td>Flicker - Data transmitting and receiving</td></tr>
        <tr><td rowspan="3">LoRa LED</td><td>ON - LoRa is working</td></tr>
        <tr><td>OFF - LoRa is not working</td></tr>
        <tr><td>Flicker - Indicate LoRa Packet receiving and sending</td></tr>
        <tr><td rowspan="8">WLAN LED</td><td>AP Mode:</td></tr>
        <tr><td>-ON - the AP is up</td></tr>
        <tr><td>-OFF - The AP is down</td></tr>
        <tr><td>-Flicker - Data receiving and sending</td></tr>
        <tr><td>STA Mode:</td></tr>
        <tr><td>-Slow flicker (1 Hz) - Disconnected</td></tr>
        <tr><td>-ON - Connected</td></tr>
        <tr><td>-Flicker - Data receiving and sending</td></tr>
        <tr><td rowspan="3">LTE LED (functional
only in RAK7268CV2)</td><td>Slow Flicker (1800&nbsp;ms High / 200&nbsp;ms Low) - Network searching</td></tr>
        <tr><td>Slow flicker (200&nbsp;ms High / 1800&nbsp;ms Low) - Idle</td></tr>
        <tr><td>Fast flicker (125&nbsp;ms High / 125&nbsp;ms Low) - Ongoing data transfer</td></tr>
    </tbody>
</table>

#### RF Specifications

##### Wi-Fi Radio Specifications

<table>
    <thead><tr><th>Feature</th><th>Specifications</th></tr></thead>
    <tbody>
        <tr><td>Wireless Standard</td><td>IEEE 802.11b/g/n</td></tr>
        <tr><td>Operating Frequency</td><td>ISM band: 2.412~2.472&nbsp;GHz</td></tr>
        <tr><td>Operation Channels</td><td>2.4&nbsp;GHz: 1-13</td></tr>
        <tr><td rowspan="11">Transmit Power (The max power maybe different depending on local regulations) - per chain</td><td>802.11b</td></tr>
        <tr><td>  19&nbsp;dBm @1&nbsp;Mbps</td></tr>
        <tr><td>  19&nbsp;dBm @11&nbsp;Mbps</td></tr>
        <tr><td>802.11g</td></tr>
        <tr><td>  18&nbsp;dBm @6&nbsp;Mbps</td></tr>
        <tr><td>  16&nbsp;dBm @&nbsp;Mbps</td></tr>
        <tr><td>  802.11n (2.4&nbsp;G)</td></tr>
        <tr><td>  18&nbsp;dBm @MCS0 (HT20)</td></tr>
        <tr><td>  16&nbsp;dBm @MCS7 (HT20)</td></tr>
        <tr><td>  17&nbsp;dBm @MCS0 (HT40)</td></tr>
        <tr><td>  15&nbsp;dBm @MCS7 (HT40)</td></tr>
        <tr><td rowspan="11">Receiver Sensitivity (Typical)</td><td>802.11b</td></tr>
        <tr><td>  -95&nbsp;dBm @1&nbsp;Mbps</td></tr>
        <tr><td>  -88&nbsp;dBm @11&nbsp;Mbps</td></tr>
        <tr><td>802.11g</td></tr>
        <tr><td>  -90&nbsp;dBm @6&nbsp;Mbps</td></tr>
        <tr><td>  -75&nbsp;dBm @54&nbsp;Mbps</td></tr>
        <tr><td>  802.11n (2.4&nbsp;G)</td></tr>
        <tr><td>  -89&nbsp;dBm @MCS0 (HT20)</td></tr>
        <tr><td>  -72&nbsp;dBm @MCS7 (HT20)</td></tr>
        <tr><td>  -86&nbsp;dBm @MCS0 (HT40)</td></tr>
        <tr><td>  -68&nbsp;dBm @MCS7 (HT40)</td></tr>
    </tbody>
</table>

##### LoRa Radio Specifications


<table>
    <thead>
      <tr><th>Feature</th><th>Specifications</th></tr>
    </thead>
    <tbody>
        <tr><td>Operating Frequency</td><td>EU433/CN470/EU868/US915/AS923/AU915/IN865/KR920</td></tr>
        <tr><td>Transmit Power</td><td>27&nbsp;dBm (Max)</td></tr>
        <tr><td>Receiver Sensitivity</td><td>-139&nbsp;dBm (Min)</td></tr>
</tbody>
</table>

##### LTE Radio Specifications (optional, available with RAK7268CV2)


<table>
    <thead><tr><th>Feature</th><th>Specifications</th></tr></thead>
    <tbody>
    <tr><td rowspan="3">EG95-E for EMEA Region</td><td>LTE FDD: B1/B3/B7/B8/B20/B28A </td></tr>
    <tr><td>WCDMA: B1/B8s</td></tr>
    <tr><td>GSM/EDGE: B3/B8</td></tr>
    <tr><td rowspan="3">EG95-NA for North America Region</td><td>LTE FDD: B2/B4/B5/B12/B13 </td></tr>
    <tr><td>WCDMA: B2/B4/B5</td></tr>
    <tr><td>Optional supports other PCIE LTE module for Global Region</td></tr>
</tbody>
</table>

#### Antennas

Depending on the frequency range, the included LoRa antenna will be as follows:

- Frequency Range 863~870&nbsp;MHz - [RAKARJ15 868&nbsp;MHz White Blade Antenna](https://docs.rakwireless.com/Product-Categories/Accessories/RAKARJ15/Overview/#features)
- Frequency Range 902~928&nbsp;MHz - [RAKARJ14 915&nbsp;MHz White Blade Antenna](https://docs.rakwireless.com/Product-Categories/Accessories/RAKARJ14/Overview/)

#### Electrical Characteristics

The Gateway comes with a 12&nbsp;V - 1&nbsp;A power adaptor. It is also fully compatible with PoE (IEEE 802.3af), 36~57&nbsp;VDC. The typical power consumption is 12&nbsp;W.

#### Mechanical Characteristics

<table>    
    <thead>
        <tr><th>Parameter</th><th colspan="3">Value</th></tr>
    </thead>    
    <tbody>        
        <tr><td>Dimensions</td>
            <td>166 x 127.5 x 36&nbsp;mm Gateway only (no antenna, no bracket)</td>
        </tr>  
        <tr><td>Weight</td><td>0.3&nbsp;kg</td></tr>    
        <tr><td>Ingress protection</td><td>IP30</td></tr>
    </tbody>
</table>

#### Environmental Requirements

The casing is IP30 rated and is made of plastic. There are holes for a mounting bracket on the back, to simplify wall mounting. The enclosure, while robust, is not meant for outdoor deployment and should be kept away from moisture.


<table>
    <thead><tr><th>Parameter</th><th>Value</th></tr></thead>
    <tbody>
        <tr><td>Dimensions</td><td>166 x 127.5 x 36&nbsp;mm</td></tr>
        <tr><td>Weight</td><td>0.3&nbsp;kg</td></tr>
        <tr><td>Operating temperature</td><td>-10&nbsp;°C to 55&nbsp;°C</td></tr>
</tbody>
</table>

### Software

#### Software Features

<table>
    <thead>
        <tr><th>LoRaWAN</th><th>Network</th><th>Management</th></tr>
    </thead>
    <tbody>
        <tr><td>Gateway OTA management</td><td> </td><td>WisDM</td></tr>
        <tr><td>LoRa package forward (packet forwarder, Basics Station)</td><td>Uplink backup</td><td>SSH2</td></tr>
        <tr><td>Country code setup</td><td>802.1q</td><td>Firmware update</td></tr>
        <tr><td>TX Power setup</td><td>DHCP Server/Client</td><td>NTP</td></tr>
        <tr><td>Data logger</td><td>Router module NAT</td><td>Configuring the LoRa Packet Forwarder</td></tr>
        <tr><td>Statistics</td><td>Firewall</td><td>Build-in Server</td></tr>
        <tr><td>Location setup</td><td>LTE APN setup</td><td>OpenVPN, Ping Watch Dog</td></tr>
        <tr><td>Server address and Port setup</td><td> </td><td>MQTT Bridge</td></tr>
        <tr><td>Supports class A, C</td><td>Wi-Fi AP mode</td><td>WEB management</td></tr>
</tbody>
</table>

### Firmware

The firmware sits on OpenWrt. There is a Web UI for easy configuration and management of the device, as well as the possibility for SSH2 management. The WisGateOS V2 supports the feature to install extensions (OpenVPN, WireGuard, Custom Logo, etc). Detailed information about the extensions can be found on the [WisGateOS 2 Extensions](https://docs.rakwireless.com/Product-Categories/Software-APIs-and-Libraries/WisGateOS-2-Extensions/Overview/#extensions).

|                   Model                    | Firmware Version |                                            Source                                            |
| :----------------------------------------: | :--------------: | :------------------------------------------------------------------------------------------: |
| RAK7268V2 / RAK7268CV2 WisGate Edge Lite 2 |      v2.2.8      | [Download](https://downloads.rakwireless.com/LoRa/WisGateOS2/WisGateOS2_Latest_Firmware.zip) |

## Certification

<rk-certifications :params="$page.frontmatter.certifications" />

### FCC Caution

Any changes or modifications not expressly approved by the party responsible for compliance could void the user's authority to operate the equipment.

This device complies with part 15 of the FCC Rules. Operation is subject to the following two conditions: (1) This device may not cause harmful interference, and (2) this device must accept any interference received, including interference that may cause undesired operation.

:::tip 📝 NOTE

This equipment has been tested and found to comply with the limits for a Class B digital device, according to part 15 of the FCC Rules. These limits are designed to provide reasonable protection against harmful interference in a residential installation. This equipment generates, uses, and can radiate radio frequency energy and, if not installed and used following the instructions, may cause harmful interference to radio communications. However, there is no guarantee that interference will not occur in a particular installation. If this equipment does cause harmful interference to radio or television reception, which can be determined by turning the equipment off and on, the user is encouraged to try to correct the interference by one or more of the following measures:

1. Reorient or relocate the receiving antenna.
2. Increase the separation between the equipment and the receiver.
3. Connect the equipment into an outlet on a circuit different from that to which the receiver is connected.
4. Consult the dealer or an experienced radio/TV technician for help.

:::

### FCC Radiation Exposure Statement

This equipment complies with FCC radiation exposure limits set forth for an uncontrolled environment. This equipment should be installed and operated with a minimum distance of 20&nbsp;cm between the radiator and your body.

### ISEDC Warning

This device complies with the Innovation, Science, and Economic Development Canada licence-exempt RSS standard(s). Operation is subject to the following two conditions:

1. This device may not cause interference;

2. This device must accept any interference, including interference that may cause undesired operation of the device.

Le présent appareil est conforme aux CNR d' Innovation, Sciences et Développement économique Canada applicables aux appareils radio exempts de licence. L'exploitation est autorisée aux deux conditions suivantes :

1. l'appareil nedoit pas produire de brouillage, et

2. l'utilisateur de l'appareil doit accepter tout brouillage radioélectrique subi, même si le brouillage est susceptible d'en compromettre le fonctionnement.

The device complies with RF exposure guidelines, users can obtain Canadian information on RF exposure and compliance. The minimum distance from the body to use the device is 20&nbsp;cm.

Le présent appareil est conforme Après examen de ce matériel aux conformité ou aux limites d’intensité de champ RF, les utilisateurs peuvent sur l’exposition aux radiofréquences et la conformité and compliance d’acquérir les informations correspondantes. La distance minimale du corps à utiliser le dispositif est de 20&nbsp;cm.
