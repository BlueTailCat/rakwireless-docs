---
rak_desc: Contains instructions and tutorials for installing and deploying your RAK7289 V2. Instructions are written in a detailed and step-by-step manner for an easier experience in setting up your device.
rak_img: /assets/images/wisgate/rak7289-v2/RAK7289V2.png
prev: ../Overview/
next: ../Supported-LoRa-Network-Servers/
tags:
  - RAK7289V2
  - RAK7289CV2
  - quickstart
  - wisgate
---

# RAK7289V2/RAK7289CV2 Quick Start Guide


## Prerequisites

### What do you need?

1. [RAK7289 V2 WisGate Edge Pro](https://store.rakwireless.com/products/wisgate-edge-pro-rak7289v2-rak7289cv2?utm_source=WisGateRAK7289V2&utm_medium=Document&utm_campaign=BuyFromStore)
2. A Windows/Mac OS/Linux Computer

:::warning ⚠️ WARNING
- The SIM card slot of the cellular versions is not hot-swappable. Make sure the gateway is switched off before inserting or ejecting the SIM card.
- The SD card found in the SD card slot must not be ejected, as it might affect the performance of the device, as different logs and data are stored on it.
:::


### What is Included in the Package?

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/1.package.png"
  width="60%"
  caption="RAK7289 V2 package contents"
/>


:::tip 📝 NOTE
Thе product does not include the LoRa antenna/s out of the box. The antennas are sold separately.
:::


## Product Configuration

### Installation

This section provides the instructions on mounting and securing the mounting kit to the enclosure and the mounting pole.

#### Mounting

1. Fix the bracket included in the mounting kit on the bottom of the enclosure with four M6*12 screws.

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/2.mounting.png"
  width="50%"
  caption="Mounting the bracket to the enclosure"



2. Position and tighten the pole clamps together around the pole with bolts, washers, and nuts. 

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/3.clamps.png"
  width="60%"
  caption="Mounting the clamps to a pole"
/>

:::tip 📝 NOTE

The diameter of the pole that is supported by the brackets is 50-100&nbsp;mm. If the pole diameter is more than this value, hose clamps can be used. The standard mounting kit does not include hose clamps. If needed, they should be purchased separately. 

:::

The clamp's back also has openings for hose clamps that are not included in the mounting kit.

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/4.hose-clamps.png"
  width="35%"
  caption="Mounting using hose clamps"

3. Hang up the enclosure and fasten it with two M6*12 screws.

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/5.fasten-enclosure.png"
  width="50%"
  caption="Fastening the enclosure to the bracket"
/>

#### Connecting the PoE Adapter

1. Connect the Ethernet cable from the enclosure to the Ethernet port labeled PoE adapter.
2. Connect an Ethernet cable from your LAN network to the Ethernet port labeled LAN on the adapter.
3. Connect one end of the power cord to the adapter. Connect the other end of the power cord to a power outlet. 

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/6.poe-adapter.png"
  width="50%"
  caption="Connecting the PoE adapter"
/>


#### Weather Protection

To better protect the Ethernet cable gland and the antenna connector from the weather, you need to cover them with PVC tape.

1. Clean the surface area of the connector that will be wrapped. Wrap a layer of PVC tape with a 50% overlap according to the rotation direction of the connector. Continue wrapping the PVC tape to about 10&nbsp;mm below the end of the connector. 

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/7.pvc-tape.png"
  width="40%"
  caption="Wrapping with PVC tape"
/>

2. Cut off about 50&nbsp;cm waterproof tape. Stretch it to double the length. Wrap three layers around the connector with a 50% overlap. Hold the tape in place with your hand for a few seconds.

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/8.waterproof-tape.png"
  width="40%"
  caption="Wrapping with waterproof tape"
/>

3. Wrap three additional layers with PVC tape with natural uncoiling force and a 50% overlap. Make sure to cover the head and the tail of the connector. 

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/9.pvc-wrapping.png"
  width="40%"
  caption="Final PVC wrapping"
/>


#### Lightning Protection
In this section, how to set up lightning surge protection system, whether your RAK7289 V2 WisGate Edge Pro V2 is situated outdoor or indoor, will be discussed. Such a protection system must be taken into consideration to ensure a fully functional gateway without interruption or damage from the lighting.               

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/10.lightning-protection.jpg"
  width="90%"
  caption="Full lightning protection set-up"
/>

##### Outdoor Surge Protection System

- **Antenna Grounding** - RAKwireless recommends a lightning arrestor to be installed on all the antenna N-type terminals. The arrestors have to be N-type Female to Male in order to fit the antenna and enclosure connectors. Make sure you use a 10 AWG or better wire to connect the screw terminals of the arrestors to the grounding rail mounted on the building wall (grounding bar in case of field deployment).
- **Gateway Grounding** - Additionally, it is recommended to use another 10 AWG or better grounding wire to connect the screw terminal on the bottom left side of the gateway casing to the grounding rail (bar).

:::tip 📝 NOTE
No additional protection for the Ethernet cabling is required at the gateway side. There is a surge protection system built-in (GDT + Anti-surge resistor).            
:::

##### Indoor Surge Protection

For protecting the indoor equipment and circuitry connected to the gateway, it is recommended to install an Ethernet port SPD lightning arrestor. It should be positioned along the cabling connecting the gateway to the PoE injector. Make sure you connect its grounding wire terminal to an appropriate building grounding point.


:::warning ⚠️ WARNING

Should you fail to adhere to the recommendations in this document RAKwireless carries no responsibility for any damage your equipment incurs due to a lightning strike.

:::

#### Recommended Equipment

- [Lightning arrestor for the LoRa antennas](https://store.rakwireless.com/products/lightning-arrestor) - This is a surge protective device for securing transceivers against over-voltage and surge current induced by bolts of lightning. RAKwireless recommends installing a lightning arrestor on all LoRa N-type antenna terminals.  

- [Pulsar cable RAK9731](https://store.rakwireless.com/products/pulsar-cable-rak9731-rak9733?variant=39677580968134) - RAK9731 Pulsar cable is used for RAK7289 V2 Lightning Protection. This cable is an N-Type Male - N-Type Female cable with 1.5 m, 3 m, 5 m, 10 m, or longer custom lengths. It is an LMR-400 coaxial cable with N-type connectors.

- [Signal Surge Protective Device](https://store.rakwireless.com/products/signal-surge-protective?variant=29842390122541) - This surge protective device is suitable for Category 6 cable or Class E cable for the protection of equipment from surge and over-voltage induced by lightning or produced in the inner systems. It is widely used in office and industry comprehensive network wiring projects or similar telecommunication applications, such as Gigabit Ethernet, ATM, ISDN, and VoIP systems.

- [Ethernet Cabling](https://store.rakwireless.com/products/cat5-ethernet-cable) - A CAT5 Ethernet Cable is recommended for an outdoor surge protection system. It is used for connections between the PoE injector, Ethernet SPD, router/switch, and the Ethernet/PoE port on RAK7289. 

### Power on the Gateway

In this section, it is assumed that you have read and performed the procedures listed in the **Installation** part of this document. 

1. Attach all antennas to the Gateway (one LoRa antenna for 8-channel gateways, two LoRa antennas for 16-channel gateways).

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/11.attached-antenna.png"
  width="20%"
  caption="RAK7289 V2 with attached antennas"
/>

2. Power on the gateway. It is recommended to use **CAT5 Cable** to provide power to the gateway. Attach one end to the **PoE injector** and the other to the **Ethernet Port** on the bottom of the casing.

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/12.powering-the-gateway.jpg"
  width="70%"
  caption="Powering the gateway using PoE"
/>


### Access the Gateway

In this section, several ways of accessing the gateway are provided to have different alternatives for you to choose from depending on the availability of the requirements needed.

:::warning ⚠️ WARNING

Do not power the device if the LoRa antenna port has been left open to avoid potential damage to the RAK7289 V2 WisGate Edge Pro.

::: 


#### Wi-Fi AP Mode

By default, the gateway will work in Wi-Fi AP Mode, which means that you can find an SSID, named **"RAK7289_XXXX"** on your PC's Wi-Fi Network List. **"XXXX"** is the last two bytes of the Gateway MAC address. 

To access the Web Management Platform, input the IP Address **192.168.230.1** in your Web browser.


<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/13.access-the-gateway.jpg"
  width="70%"
  caption="Accessing the gateway via Wi-Fi AP mode"
/>


:::tip 📝 NOTE

No password is required to connect via Wi-Fi.

:::


2. Using your preferred Web browser, input the aforementioned IP address and you should see the Login Page. Login with the provided credentials.

- **Username:** root
- **Password:** root


#### WAN Port (Ethernet)

1. Connect the Ethernet cable to the port marked **ETH** on the gateway and the other end to the PoE port of the PoE injector. Connect the LAN port of the PoE injector to your PC. 

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/14.wan-port.jpg"
  width="70%"
  caption="Accessing the gateway via WAN Port (Ethernet)"
/>

2. The default IP is **169.254.X.X**, where the last two segments are mapped from the last four bits of the MAC address of your gateway. For example, the last four bits of the MAC address are 0F:01 and the IP address is `169.254.15.1`. Make sure to manually set the address of your PC to one in the same network (for example, `169.254.15.100`).

3. To do this, open the head to the **Ethernet Properties** and click the **Internet Protocol Version 4 (TCP/IPv4)**.
<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/15.internet-properties.png"
  width="45%"
  caption="Internet properties"
/>

4. Select **Use the following IP address** and set the IP address (for example, `169.254.15.100`).

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/16.set-ip-address.png"
  width="45%"
  caption="Setting IP address of the PC"
/>

In this example, you can access the gateway on the `169.254.15.1` address.

####  3.3 Set Login Password

1. For security reasons, upon the first login, you must set a login password. This is done by filling in the desired password and confirming it in the provided fields. The password needs to comply with the following rules:

- Should be at least 12 characters long;
- Has at least one special character (!“#$%&\‘()*+,-./:;<=>?@[]^_`{|}~);
- Has at least one number;
- Has at least one standard Latin letter (used in the English alphabet).

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/17.web-ui.png"
  width="100%"
  caption="Web UI login page"
/>


2. When the fields are filled in, click the **Set password** button to apply it. The Web UI is now accessible and it will load the **LoRaWAN Statistics page**.


<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/18.stat-page.png"
  width="100%"
  caption="LoRaWAN statistics page"
/>



3. On the next login, you need to use the set password for access. The default login username is **root**.

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/19.set-password.png"
  width="100%"
  caption="Login Page with set password"
/>

### Access the Internet

#### Connect Through WI-FI


<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/20.access-using-wifi.jpg"
  width="50%"
  caption="Accessing the Internet using Wi-Fi"
/>


1. Access the gateway's Web UI. Navigate to **Network** > **WAN** > **Wi-Fi**. Expand the Wi-Fi block and click on **Settings**. Make sure the **Interface** is enabled.
   
- For additional information, check the [WisGateOS 2 User manual](https://docs.rakwireless.com/Product-Categories/Software-APIs-and-Libraries/WisGateOS-2/Overview/#overview).

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/21.wifi-settings.png"
  width="50%"
  caption="Wi-Fi settings"
/>


2. You can either click the **Scan** button to choose your **ESSID** or manually type the ESSID of the network by clicking **enter network (E)SSID manually**.
3. Select the right **Encryption** method and enter the correct **Key**.

:::tip 📝 NOTE
Assuming you have entered the correct parameter values, you should get an IP address assigned by your Wi-Fi router's (AP) built-in DHCP server. You can use this new IP address to log in via a web browser (the same way as in AP mode).
:::

#### Connect Through Ethernet/PoE

<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/22.access-thru-ethernet.jpg"
  width="50%"
  caption="Accessing the Internet through Ethernet"
/>

1. Connect the Ethernet cable to the port marked **ETH** on the gateway and the other end to the PoE port of the PoE injector. 
2. Connect the LAN port of the PoE injector to your router. The router's DHCP server should assign an IP Address to the gateway. 
3. Now, you can access the assigned IP to access the gateway. You can change the default settings below if you wish (details in the [WisGate2 OS User Manual](https://docs.rakwireless.com/Product-Categories/Software-APIs-and-Libraries/WisGateOS-2/Overview/#overview)).


<rk-img
  src="/assets/images/wisgate/rak7289-v2/quickstart/23.ethernet-settings.png"
  width="45%"
  caption="Connect through Ethernet settings"
/>  

