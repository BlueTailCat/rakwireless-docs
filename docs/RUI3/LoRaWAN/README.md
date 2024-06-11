# LoRaWAN

:::warning ⚠️ WARNING
With version V4.1.1 of RUI3, the LoRa P2P functions are separated into a new class and API calls for LoRa have a changed syntax:

| Old                        | New                     | Comment                                          |
|----------------------------|-------------------------|--------------------------------------------------|
| `api.lorawan.pXXX`         | `api.lora.pXXX`        | All LoRa P2P API calls change.                   |
| `api.lorawan.registerPyyy` | `api.lora.registerPyyy` | All LoRa P2P callback register API calls change. |
| `api.lorawan.nwm.set(1)`   | `api.lorawan.nwm.set()` | Set device to LoRaWAN mode.                      |
| `api.lorawan.nwm.set(0)`   | `api.lora.nwm.set()`    | Set device to LoRa P2P mode.                     |

:::


## LoRaWAN Data Type

### RAK\_LORA\_McSession

The structure of a multicast group

```c
typedef struct
{
  uint8_t McDevclass;     ///< The device class of a multicast group
  uint32_t McAddress;     ///< The address of a multicast group
  uint8_t McAppSKey[16];  ///< The application session key of a multicast group
  uint8_t McNwkSKey[16];  ///< The Network session key of a multicast group
  uint32_t McFrequency;   ///< The frequency of a multicast group
  int8_t McDatarate;      ///< The data rate of a multicast group
  uint16_t McPeriodicity; ///< The periodicity of a multicast group
  int8_t McGroupID;       ///< The group ID of a multicast group
  uint8_t entry;          ///< The entry of a multicast group
} RAK_LORA_McSession;
```

#### McDevclass

The device class of a multicast group

```c
uint8_t McDevclass
```

#### McAddress

The address of a multicast group

```c
uint32_t McAddress
```

#### McAppSKey

The application session key of a multicast group

```c
uint8_t McAppSKey[16]
```

#### McNwkSKey

The Network session key of a multicast group

```c
uint8_t McNwkSKey[16]
```

#### McFrequency

The frequency of a multicast group

```c
uint32_t McFrequency
```

#### McDatarate

The data rate of a multicast group

```c
int8_t McDatarate
```

#### McPeriodicity

The periodicity of a multicast group

```c
uint16_t McPeriodicity
```

#### McGroupID

The group ID of a multicast group

```c
int8_t McGroupID
```

#### entry

The entry of a multicast group

```c
uint8_t entry
```


### RAK\_LORA\_chan\_rssi\_t

The structure of a rssi data

```c
typedef struct
{
  uint32_t chan; ///< The channel of a rssi
  uint16_t mask; ///< The mask of a rssi
  int8_t rssi;   ///< The rssi on reception
} RAK_LORA_chan_rssi;"
```

#### chan

The channel of a rssi

```c
uint32_t chan
```


#### mask

The mask of a rssi

```c
uint16_t mask
```

#### rssi

The rssi on reception

```c
int8_t rssi
```



### RAK\_LORA\_BAND

The regions of LoRa

```c
enum _RAK_LORA_BAND
```


| Enumerator         |             |
| ------------------ | ----------- |
| RAK_REGION_EU433   | EU433       |
| RAK_REGION_CN470   | CN470 ~ 510 |
| RAK_REGION_RU864   | RU864 ~ 870 |
| RAK_REGION_IN865   | IN865 ~ 867 |
| RAK_REGION_EU868   | EU863 ~ 870 |
| RAK_REGION_US915   | US902 ~ 928 |
| RAK_REGION_AU915   | AU915 ~ 928 |
| RAK_REGION_KR920   | KR920 ~ 923 |
| RAK_REGION_AS923-1 | AS923-1     |
| RAK_REGION_AS923-2 | AS923-2     |
| RAK_REGION_AS923-3 | AS923-3     |
| RAK_REGION_AS923-4 | AS923-4     |
| RAK_REGION_LA915   | LA915       |

```c
typedef enum
{
  RAK_REGION_EU433 = 0, ///< EU433
  RAK_REGION_CN470 = 1, ///< CN470 ~ 510
  RAK_REGION_RU864 = 2, ///< RU864 ~ 870
  RAK_REGION_IN865 = 3, ///< IN865 ~ 867
  RAK_REGION_EU868 = 4, ///< EU863 ~ 870
  RAK_REGION_US915 = 5, ///< US902 ~ 928
  RAK_REGION_AU915 = 6, ///< AU915 ~ 928
  RAK_REGION_KR920 = 7, ///< KR920 ~ 923
  RAK_REGION_AS923_1 = 8, ///< AS923-1
  RAK_REGION_AS923_2 = 9, ///< AS923-2
  RAK_REGION_AS923_3 = 10, ///< AS923-3
  RAK_REGION_AS923_4 = 11, ///< AS923-4
  RAK_REGION_LA915 = 12, ///< LA915
} RAK_LORA_BAND;"

```

### RAK\_LORA\_JOIN\_MODE

The LoRaWAN network join modes

```c
enum _RAK_LORA_JOIN_MODE
```
| Enumerator    |                               |
| ------------- | ----------------------------- |
| RAK_LORA_ABP  | activation by personalization |
| RAK_LORA_OTAA | over-the-air activation       |


```c
typedef enum
{
  RAK_LORA_ABP = 0, ///< activation by personalization
  RAK_LORA_OTAA = 1 ///< over-the-air activation
} RAK_LORA_JOIN_MODE;
```

### RAK\_LORA\_WORK\_MODE

The LoRaWAN working modes

```c
enum _RAK_LORA_WORK_MODE
```

| Enumerator   |                        |
| ------------ | ---------------------- |
| RAK_LORA_P2P | Switch to P2P mode     |
| RAK_LORAWAN  | Switch to LoRaWAN mode |
| RAK_LORA_FSK | Switch to FSK mode     |

```c
typedef enum
{
  RAK_LORA_P2P = 0, ///< Switch to P2P mode
  RAK_LORAWAN = 1,  ///< Switch to LoRaWan mode
  RAK_LORA_FSK = 2, ///< Switch to FSK mode
} RAK_LORA_WORK_MODE;"
```

### RAK\_LORA\_CONFIRM\_MODE

The status of confirm mode

```c
enum _RAK_LORA_CONFIRM_MODE
```

| Enumerator      |                                                     |
| --------------- | --------------------------------------------------- |
| RAK_LORA_NO_ACK | The device will not get received data from network. |
| RAL_LORA_ACK    | The device will get received data from network.     |

```c
typedef enum
{
  RAK_LORA_NO_ACK = 0, ///< The device will not get received data from network
  RAL_LORA_ACK = 1,    ///< The device will get received data from network
} RAK_LORA_CONFIRM_MODE;
```



### RAK\_LORA\_CLASS

The LoRaWAN classes

```c
enum _RAK_LORA_CLASS

```

| Enumerator       |                                   |
| ---------------- | --------------------------------- |
| RAK_LORA_CLASS_A | The LoRaWAN will work in Class A. |
| RAK_LORA_CLASS_B | The LoRaWAN will work in Class B. |
| RAK_LORA_CLASS_C | The LoRaWAN will work in Class C. |

```c
typedef enum
{
  RAK_LORA_CLASS_A = 0, ///< The LoRaWan will work in Class A
  RAK_LORA_CLASS_B = 1, ///< The LoRaWan will work in Class B
  RAK_LORA_CLASS_C = 2, ///< The LoRaWan will work in Class C
} RAK_LORA_CLASS;"
```

### SERVICE\_LORA\_RECEIVE\_T

The LoRaWAN receive frame control structure

```c
   typedef struct SERVICE_LORA_RECEIVE
    {
        uint8_t Port;
        uint8_t RxDatarate;
        uint8_t *Buffer;
        uint8_t BufferSize;
        int16_t Rssi;
        int8_t Snr;
        uint32_t DownLinkCounter;
    } SERVICE_LORA_RECEIVE_T;

```

#### Port

Application port

```c
uint8_t Port
```

#### RxDatarate

Downlink datarate

```c
uint8_t RxDatarate;
```

#### Buffer

Pointer to the received LoRaWAN data stream

```c
uint8_t *Buffer;
```
#### BufferSize

Size of the received LoRaWAN data stream

```c
uint8_t BufferSize;
```
#### Rssi

Rssi of the LoraWAN received packet

```c
int16_t Rssi;
```

#### Snr

Signal-to-noise ratio of the LoRaWAN received packet

```c
int8_t Snr;
```

####  DownLinkCounter

The downlink counter value for the received frame

```c
uint32_t DownLinkCounter;
```

###  rui\_lora\_p2p\_revc\_t

The LoRa P2P receive frame control structure

```
typedef struct rui_lora_p2p_revc
{

    uint8_t *Buffer;
    uint8_t BufferSize;
    int16_t Rssi;
    int8_t Snr;
} rui_lora_p2p_recv_t;

```
#### Buffer

Pointer to the received LoRa P2P data stream

```c
uint8_t *Buffer;
```
#### BufferSize

Size of the received LoRa P2P data stream

```c
uint8_t BufferSize;
```
#### Rssi

Rssi of the received LoRa P2P packet

```c
int16_t Rssi;
```

#### Snr

Signal-to-noise ratio of the received P2P packet

```c
int8_t Snr;
```

### RAKLoRaMacEventInfoStatus

The Mac event results can be received in RX, TX, and Join callbacks.

| Enumerator                                         | Description                                                                                                                                               |
| -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `RAK_LORAMAC_STATUS_OK`                            | Service performed successfully                                                                                                                            |
| `RAK_LORAMAC_STATUS_ERROR`                         | An error occurred during the execution of the service                                                                                                     |
| `RAK_LORAMAC_STATUS_TX_TIMEOUT`                    | A Tx timeout occurred                                                                                                                                     |
| `RAK_LORAMAC_STATUS_RX1_TIMEOUT`                   | An Rx timeout occurred on receive window 1                                                                                                                |
| `RAK_LORAMAC_STATUS_RX2_TIMEOUT`                   | An Rx timeout occurred on receive window 2                                                                                                                |
| `RAK_LORAMAC_STATUS_RX1_ERROR`                     | An Rx error occurred on receive window 1                                                                                                                  |
| `RAK_LORAMAC_STATUS_RX2_ERROR`                     | An Rx error occurred on receive window 2                                                                                                                  |
| `RAK_LORAMAC_STATUS_JOIN_FAIL`                     | An error occurred in the join procedure                                                                                                                   |
| `RAK_LORAMAC_STATUS_DOWNLINK_REPEATED`             | A frame with an invalid downlink counter was received. The downlink counter of the frame is equal to the local copy of the downlink counter of the node. |
| `RAK_LORAMAC_STATUS_TX_DR_PAYLOAD_SIZE_ERROR`      | The MAC could not retransmit a frame since the MAC decreased the data rate. The payload size does not apply to the data rate.                             |
| `RAK_LORAMAC_STATUS_DOWNLINK_TOO_MANY_FRAMES_LOSS` | The node has lost `MAX_FCNT_GAP` or more frames.                                                                                                          |
| `RAK_LORAMAC_STATUS_ADDRESS_FAIL`                  | An address error occurred                                                                                                                                 |
| `RAK_LORAMAC_STATUS_MIC_FAIL`                      | Message integrity check failure                                                                                                                           |
| `RAK_LORAMAC_STATUS_MULTICAST_FAIL`                | Multicast error occurred                                                                                                                                  |
| `RAK_LORAMAC_STATUS_BEACON_LOCKED`                 | Beacon locked                                                                                                                                             |
| `RAK_LORAMAC_STATUS_BEACON_LOST`                   | Beacon lost                                                                                                                                               |
| `RAK_LORAMAC_STATUS_BEACON_NOT_FOUND`              | Beacon not found                                                                                                                                          |

```c
   typedef enum RAKLoRaMacEventInfoStatus {
  RAK_LORAMAC_STATUS_OK = 0,
  RAK_LORAMAC_STATUS_ERROR,
  RAK_LORAMAC_STATUS_TX_TIMEOUT,
  RAK_LORAMAC_STATUS_RX1_TIMEOUT,
  RAK_LORAMAC_STATUS_RX2_TIMEOUT,
  RAK_LORAMAC_STATUS_RX1_ERROR,
  RAK_LORAMAC_STATUS_RX2_ERROR,
  RAK_LORAMAC_STATUS_JOIN_FAIL,
  RAK_LORAMAC_STATUS_DOWNLINK_REPEATED,
  RAK_LORAMAC_STATUS_TX_DR_PAYLOAD_SIZE_ERROR,
  RAK_LORAMAC_STATUS_DOWNLINK_TOO_MANY_FRAMES_LOSS,
  RAK_LORAMAC_STATUS_ADDRESS_FAIL,
  RAK_LORAMAC_STATUS_MIC_FAIL,
  RAK_LORAMAC_STATUS_MULTICAST_FAIL,
  RAK_LORAMAC_STATUS_BEACON_LOCKED,
  RAK_LORAMAC_STATUS_BEACON_LOST,
  RAK_LORAMAC_STATUS_BEACON_NOT_FOUND
};

```

## LoRa Network Management

### nwm

Switch to LoRaWAN mode

```c
RAKLorawan::nwm
```

#### get()

This API gets the network working mode (0 = P2P, 1 = LoRaWAN, 2 = FSK).

```c
api.lorawan.nwm.get();
```


| **Function**      | `int get()`                                                      |
| ----------------- | ---------------------------------------------------------------- |
| **Returns**       | the network working mode                                         |
| **Return Values** | **0** - P2P mode <br> **1** - LoRaWAN mode <br> **2** - FSK mode |



::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the network working mode %s\r\n", api.lorawan.nwm.set() ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network working mode = %s\r\n", api.lorawan.nwm.get() ? "LoRaWan" : "P2P");

    delay(1000);
}
```
:::

#### set()

This API sets the network working mode to LoRaWAN.

```c
api.lorawan.nwm.set();
```

| **Function**      | `bool set()	`                                                                                 |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| **Returns**       | bool                                                                                                       |
| **Return Values** | **TRUE** for setting network working mode success <br>  **FALSE** for setting network working mode failure |

::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the network working mode %s\r\n", api.lorawan.nwm.set() ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network working mode = %s\r\n", api.lorawan.nwm.get() ? "LoRaWan" : "P2P");

    delay(1000);
}

```
:::



### adr

This API allows the user to access the adaptive data rate.

```c
RAKLorawan::adr
```

::: tip 📝 NOTE
The default value of the ADR is 1 (enabled).
:::

#### get()

This API allows the user to get the enabled/disabled status of adaptive data rate.

```c
api.lorawan.adr.get();
```

| **Function**      | `bool get()`                                                                      |
| ----------------- | --------------------------------------------------------------------------------- |
| **Returns**       | bool                                                                              |
| **Return Values** | **TRUE** - adaptive data rate enabled <br> **FALSE** - adaptive data rate disabled |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set adaptive data rate %s\r\n", api.lorawan.adr.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Adaptive data rate is  %s\r\n", api.lorawan.adr.get() ? "Enable" : "Disable");
    delay(1000);
}
```
:::

#### set()

This API allows the user to enable/disable the adaptive data rate.

```c
api.lorawan.adr.set(value);
```

| **Function**      | `bool set(bool value)`                                                                        |
| ----------------- | --------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the status of adaptive data rate <br> - TRUE ADR enabled <br> - FALSE ADR disabled |
| **Returns**       | bool                                                                                          |
| **Return Values** | **TRUE** for setting status of adr success  <br>  **FALSE** for setting status of adr failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set adaptive data rate %s\r\n", api.lorawan.adr.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Adaptive data rate is  %s\r\n", api.lorawan.adr.get() ? "Enable" : "Disable");
    delay(1000);
}
```
:::


### deviceClass

This API allows the user to access the LoRaWAN class.

```c
RAKLorawan::deviceClass
```

#### get()

This API allows the user to get the LoRaWAN class.

```c
api.lorawan.deviceClass.get();
```

| **Function**      | `uint8_t get()`                                           |
| ----------------- | --------------------------------------------------------- |
| **Returns**       | the **LoRaWan** class (Type: **int**)                     |
| **Return Values** | **0** - Class A <br> **1** - Class B <br> **2** - Class C |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set device class to Class_A  %s\r\n", api.lorawan.deviceClass.set(0) ? "Success" : "Fail");
}

void loop()
{
    switch(api.lorawan.deviceClass.get()) {
        case 0:
            Serial.println("Device is in Class A");
            break;
        case 1:
            Serial.println("Device is in Class B");
            break;
        case 2:
            Serial.println("Device is in Class C");
            break;
    }

    delay(1000);
}
```
:::


#### set()

This API allows the user to set the LoRaWAN class.

```c
api.lorawan.deviceClass.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the LoRaWAN class <br> **0** - Class A <br> **1** - Class B <br> **2** - Class C                                                              |
| **Returns**       | bool                                                                                        |
| **Return Values** | **TRUE** for setting LoRaWAN class success <br> **FALSE** for setting LoRaWAN class failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set device class to Class_A  %s\r\n", api.lorawan.deviceClass.set(0) ? "Success" : "Fail");
}

void loop()
{
    switch(api.lorawan.deviceClass.get()) {
        case 0:
            Serial.println("Device is in Class A");
            break;
        case 1:
            Serial.println("Device is in Class B");
            break;
        case 2:
            Serial.println("Device is in Class C");
            break;
    }

    delay(1000);
}
```
:::


### dcs

This api allows the user to enable/disable the duty cycle setting

```c
RAKLorawan::dcs
```

#### get()

This API allows the user to get the duty cycle parameter.

```c
api.lorawan.dcs.get();
```

| **Function**      | `bool get()`                                                      |
| ----------------- | ----------------------------------------------------------------- |
| **Returns**       | bool                                                              |
| **Return Values** | **TRUE** - duty cycle enabled <br> **FALSE** - duty cycle disabled |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Enable duty cycle  %s\r\n", api.lorawan.dcs.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Duty cycle is  %s\r\n", api.lorawan.adr.get() ? "Enable" : "Disable");
    delay(1000);
}
```
:::


#### set()


This API allows the user to enable/disable the duty cycle.


```c
api.lorawan.dcs.set(dutyCycle);
```


| **Function**      | `bool set(uint8_t dutyCycle)`                                                       |
| ----------------- | ----------------------------------------------------------------------------------- |
| **Parameters**    | **dutyCycle** - the LoRaWAN duty cycle   <br> - **TRUE** - enable duty cycle <br> - **FALSE** - disable duty cycle                                            |
| **Returns**       | bool                                                                                |
| **Return Values** | **TRUE** for setting duty cycle success  <br> **FALSE** for setting duty cycle fail |



::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Enable duty cycle  %s\r\n", api.lorawan.dcs.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Duty cycle is  %s\r\n", api.lorawan.adr.get() ? "Enable" : "Disable");
    delay(1000);
}
```
:::


### dr

This API allows the user to access the data rate.

:::tip 📝 NOTE:
Complete information about DR parameter on each region can be found on <a href="https://docs.rakwireless.com/RUI3/Appendix/#data-rate-by-region" target="_blank">RUI3 Appendix - LoRaWAN Regional Parameter (Data Rate)</a>.
- **EU433 / RU864 / IN865 / EU868 / CN470 / KR920** and the data rate range of values is 0-5 (DR0-DR5). <br>
- **AS923** and the data rate range of values is 2-5 (DR2-DR5). <br>
- **US915** and the data rate range of values is 0-4 (DR0-DR4). <br>
- **AU915** and the data rate range of values is 0-6 (DR0-DR6). <br>
- **LA915** and the data rate range of values is 0-6 (DR0-DR6).
:::

```c
RAKLorawan::dr
```


#### get()

This API allows the user to get the data rate.

:::tip 📝 NOTE:
During the join process, the DR might be different from the defined DR. Some regions require a specific DR during the join process.
:::

```c
api.lorawan.dr.get();
```

| **Function** | `uint8_t get()` |
| ------------ | --------------- |
| **Returns**  | the data rate  (Type: **int**)  |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the data rate  %s\r\n", api.lorawan.dr.set(5) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The data rate is %d\r\n", api.lorawan.dr.get());
    delay(1000);
}
```
:::

#### set()

This API allows the user to set the data rate.


```c
api.lorawan.dr.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                               |
| ----------------- | --------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the data rate  (Type: **int**)                                                               |
| **Returns**       | bool                                                                                    |
| **Return Values** | **TRUE** for setting data rate success   <br>   **FALSE** for setting data rate failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the data rate  %s\r\n", api.lorawan.dr.set(5) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The data rate is %d\r\n", api.lorawan.dr.get());
    delay(1000);
}
```
:::


### jn1dl

This API allows the user to access the join delay on RX window 1.

```c
RAKLorawan::jn1dl
```

#### get()

This API allows the user to get the data rate.

```c
api.lorawan.jn1dl.get();
```

| **Function** | `int get()`                                   |
| ------------ | --------------------------------------------- |
| **Returns**  | the join delay on RX window 1 (Type: **int**) |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the join delay on RX window 1  %s\r\n", api.lorawan.jn1dl.set(5000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The join delay on RX window 1 is %d\r\n", api.lorawan.jn1dl.get());
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the join delay on RX window 1. The range of acceptable values is 1 to 14 seconds.

```c
api.lorawan.jn1dl.set(value);
```

| **Function**      | `bool set(int value)`                                                                 |
| ----------------- | ------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the join delay on RX window 1                                             |
| **Returns**       | bool                                                                                  |
| **Return Values** | **TRUE** for setting join delay success <br> **FALSE** for setting join delay failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the join delay on RX window 1  %s\r\n", api.lorawan.jn1dl.set(5000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The join delay on RX window 1 is %d\r\n", api.lorawan.jn1dl.get());
    delay(1000);
}
```
:::


### jn2dl


```c
RAKLorawan::jn2dl
```

#### get()

This API allows the user to access the join delay on RX window 2.

```c
api.lorawan.jn2dl.get();
```

| **Function** | `int get()`                                    |
| ------------ | ---------------------------------------------- |
| **Returns**  | the join delay on RX window 2 (Type: **int**) |


::: details Click to View Example
```c{8}
void setup()
{
    Serial.begin(115200);
}

void loop()
{
    Serial.printf("The join delay on RX window 2 is %d\r\n", api.lorawan.jn2dl.get());
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the join delay on RX window 2. The range of acceptable values is 2 to 15 seconds.

```c
api.lorawan.jn2dl.set(value);
```

| **Function**      | `bool set(int value)`                                                                 |
| ----------------- | ------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the join delay on RX window  (Type: **int**)2                                             |
| **Returns**       | bool                                                                                  |
| **Return Values** | **TRUE** for setting join delay success <br> **FALSE** for setting join delay failure |

::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the join delay on RX window 2  %s\r\n", api.lorawan.jn2dl.set(5000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The join delay on RX window 2 is %d\r\n", api.lorawan.jn2dl.get());
    delay(1000);
}
```
:::

### pnm

This API allows the user to access the public network mode.

```c
RAKLorawan::pnm
```

#### get()

This API allows the user to get the public network mode.

```c
api.lorawan.pnm.get();
```

| **Function**      | `bool get()`                     |
| ----------------- | -------------------------------- |
| **Returns**       | bool                             |
| **Return Values** | **TRUE**: On <br> **FALSE**: Off |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the public network mode  %s\r\n", api.lorawan.pnm.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The public network mode is  %d\r\n", api.lorawan.pnm.get() ? "On" : "Off");
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the public network mode.

```c
api.lorawan.pnm.set(value);
```

| **Function**      | `bool set(bool value)`                                                                                   |
| ----------------- | -------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the public network mode <br> - TRUE set public network mode <br> - FALSE set private network mode                                                                     |
| **Returns**       | bool                                                                                                     |
| **Return Values** | **TRUE** for setting public network mode success  <br> **FALSE** for setting public network mode failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the public network mode  %s\r\n", api.lorawan.pnm.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The public network mode is  %d\r\n", api.lorawan.pnm.get() ? "On" : "Off");
    delay(1000);
}
```
:::


### rx1dl

This API allows the user to access the delay of the received window 1.


```c
RAKLorawan::rx1dl
```

#### get()

This API allows the user to get the delay of the received window 1.

```c
api.lorawan.rx1dl.get();
```

| **Function** | `int get()`                        |
| ------------ | ---------------------------------- |
| **Returns**  | the delay of the received window 1 |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the received delay on RX window 1  %s\r\n", api.lorawan.rx1dl.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The received delay on RX window 1 is %d\r\n", api.lorawan.rx1dl.get());
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the delay of the received window 1. The range of acceptable values is 1 to 15&nbsp;seconds. Whenever `RX 1 Delay` is updated, `RX 2 Delay` is also updated automatically.

```c
api.lorawan.rx1dl.set(value);
```

| **Function**      | `bool set(int value)`                                                        |
| ----------------- | ---------------------------------------------------------------------------- |
| **Parameters**    | **value** - the delay of the received window 1                               |
| **Returns**       | bool                                                                         |
| **Return Values** | **TRUE** for setting delay success  <br> **FALSE** for setting delay failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the received delay on RX window 1  %s\r\n", api.lorawan.rx1dl.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The received delay on RX window 1 is %d\r\n", api.lorawan.rx1dl.get());
    delay(1000);
}
```
:::

### rx2dl

This API allows the user to access the delay of the received window 2

```c
RAKLorawan::rx2dl
```

#### get()

This API allows the user to get the delay of the received window 2

```c
api.lorawan.rx2dl.get();
```

| **Function** | `int get()`                        |
| ------------ | ---------------------------------- |
| **Returns**  | the delay of the received window 2 |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set the received delay on RX window 2  %s\r\n", api.lorawan.rx2dl.set(2000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The received delay on RX window 2 is %d\r\n", api.lorawan.rx2dl.get());
    delay(1000);
}
```
:::

#### set()

This API allows the user to set the delay of the received window 2. The range of acceptable values is 2 to 15&nbsp;seconds. Whenever `RX 2 Delay` is updated, `RX 1 Delay` is also updated automatically.

```c
api.lorawan.rx2dl.set(value)
```

| **Function**      | `bool set(int value)`                                                       |
| ----------------- | --------------------------------------------------------------------------- |
| **Parameters**    | **value** - the delay of the received window 2                              |
| **Returns**       | bool                                                                        |
| **Return Values** | **TRUE** for setting delay success <br> **FALSE** for setting delay failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the received delay on RX window 2  %s\r\n", api.lorawan.rx2dl.set(2000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The received delay on RX window 2 is %d\r\n", api.lorawan.rx2dl.get());
    delay(1000);
}
```
:::
### rx2dr

This API allows the user to access the data rate of received window 2.

```c
RAKLorawan::rx2dr
```

#### get()

This API allows the user to get the data rate of received window 2.

```c
api.lorawan.rx2dr.get();
```

| **Function** | `uint8_t get()`                    |
| ------------ | ---------------------------------- |
| **Returns**  | the data rate of received window 2 |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the data rate of received window 2 %s\r\n", api.lorawan.rx2dr.set(5) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The data rate of received window 2 is %d\r\n", api.lorawan.rx2dr.get());
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the data rate of received window 2.

```c
api.lorawan.rx2dr.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                           |
| ----------------- | ----------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the data rate of received window 2                                      |
| **Returns**       | bool                                                                                |
| **Return Values** | **TRUE** for setting data rate success <br> **FALSE** for setting data rate failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the data rate of received window 2 %s\r\n", api.lorawan.rx2dr.set(5) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The data rate of received window 2 is %d\r\n", api.lorawan.rx2dr.get());
    delay(1000);
}
```
:::


### rx2fq

```c
RAKLorawan::rx2fq
```

#### get()

This API allows the user to access the frequency of the received window 2.

```c
api.lorawan.rx2fq.get();
```

| **Function** | `long get()`                           |
| ------------ | -------------------------------------- |
| **Returns**  | the frequency of the received window 2 |


::: details Click to View Example
```c{8}
void setup()
{
    Serial.begin(115200);
}

void loop()
{
    Serial.printf("The frequency of received window 2 is %d\r\n", api.lorawan.rx2fq.get());
    delay(1000);
}
```
:::

### txp

This API allows the user to access the transmit power.

:::tip 📝 NOTE:
Highest power start from 0. Complete information about TXP parameter on each region can be found on <a href="https://docs.rakwireless.com/RUI3/Appendix/#tx-power-by-region" target="_blank">RUI3 Appendix - LoRaWAN Regional Parameter (TX Power)</a>.
- **EU868 / RU864 / KR920 / AS923 / CN470** Transmit power range of values is 0-7. <br>
- **US915 / AU915 / LA915** Transmit power range of values is 0-14. <br>
- **EU433** Transmit power range of values is 0-5. <br>
- **IN865** Transmit power range of values is 0-10.
:::

```c
RAKLorawan::txp
```

#### get()

This API allows the user to get the transmit power.


```c
api.lorawan.txp.get();
```

| **Function** | `uint8_t get()`            |
| ------------ | -------------------------- |
| **Returns**  | the LoRaWAN transmit power |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the transmit power %s\r\n", api.lorawan.txp.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The transmit power is %d\r\n", api.lorawan.txp.get());
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the transmit power.

```c
api.lorawan.txp.set(value);
```

| **Function**   | `bool set(uint8_t value)`                                                                      |
| -------------- | ---------------------------------------------------------------------------------------------- |
| **Parameters** | **value** - the LoRaWAN transmit power                                                         |
| **Returns**    | **TRUE** for setting transmit power success <br>  **FALSE** for setting transmit power failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the transmit power %s\r\n", api.lorawan.txp.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The transmit power is %d\r\n", api.lorawan.txp.get());
    delay(1000);
}
```
:::



### linkcheck

This API allows the user to verify network link status.


```c
RAKLorawan::linkcheck
```

#### get()


This API allows the user to verify network link status.

```c
api.lorawan.linkcheck.get();
```


| **Function**      | `uint32_t get()`                                                                                                                                            |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Returns**       | The mode of verifying network link status                                                                                                                   |
| **Return Values** | Link Check setting <br> - **0** link check disabled <br> - **1** execute link check one time <br> - **2** module will automatically execute a link check after every upload of data |



::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set Verifying network link status %s\r\n", api.lorawan.linkcheck.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network link status = %d\r\n", api.lorawan.linkcheck.get());

    delay(1000);
}
```
:::


#### set()

This API allows the user to set the network link status.


```c
api.lorawan.linkcheck.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                                                                              |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - 	the mode of verifying network link status  <br> - **0** link check disabled <br> - **1** execute link check one time <br> - **2** module will automatically execute a link check after every upload of data                                                                                 |
| **Returns**       | bool                                                                                                                                   |
| **Return Values** | **TRUE** for setting mode of verifying network link status <br> **FALSE**  for setting mode of verifying network link status failure ) |

::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set Verifying network link status %s\r\n", api.lorawan.linkcheck.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network link status = %d\r\n", api.lorawan.linkcheck.get());

    delay(1000);
}
```
:::


### timereq

This api allows the user to verify the status of timereq flag for next uplink and request a network time on the next uplink

#### get()

This api allows the user to get the status of timereq flag for next uplink

```c
api.lorawan.timereq.get();
```


| **Function**      | `uint8_t get()`                                                                                                                                            |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Returns**       | The status of timereq flag for next uplink                                                                                                                    |
| **Return Values** | Time request setting <br> - **0** timereq flag is disable <br> - **1** timereq flag is enable |

::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    api.lorawan.join();
    delay(10000);
    if (api.lorawan.njs.get() == 1) {
        Serial.printf("Set timereq flag %s\r\n", api.lorawan.timereq.set(1) ? "Success" : "Fail");
    }
}

void loop()
{
    Serial.printf("Get timereq flag = %d\r\n", api.lorawan.timereq.get());

    delay(1000);
}
```
:::


#### set()

This api allows the user to enable the timereq flag for next uplink.

```c
api.lorawan.timereq.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                                                                              |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - 	enable/disable time request  <br> - **0** time request disabled <br> - **1** time request enabled                                                                                 |
| **Returns**       | bool                                                                                                                                   |
| **Return Values** | **TRUE** for setting timereq flag be enable  <br> **FALSE**  for setting timereq flag be disable  |

::: details Click to View Example
```c{5}
void setup()
{
  Serial.begin(115200);

  api.lorawan.join();
  delay(10000);
  if (api.lorawan.njs.get() == 1) {
    Serial.printf("Set timereq flag %s\r\n", api.lorawan.timereq.set(1) ? "Success" : "Fail");
  }
}

void loop()
{
  Serial.printf("Get timereq flag = %d\r\n", api.lorawan.timereq.get());

  delay(1000);
}
```
:::


## Keys, IDs, and EUIs Management

### appeui

This API views or changes the LoRaWAN APPEUI and uses it to set up the LoRaWAN connection.

::: tip 📝 NOTE
This function can only work in OTAA mode.
:::


```c
RAKLorawan::appeui
```

#### get()

This API allows the user to get the global application identifier.

```c
api.lorawan.appeui.get(buf, len);
```

| **Function**      | `bool get(uint8_t * buf, uint32_t len)`                                                    |
| ----------------- | ------------------------------------------------------------------------------------------ |
| **Parameters**    | **`buf`**: the buffer to get AppEUI <br> **`len`**: the length of AppEUI (must be 8 bytes) |
| **Returns**       | bool                                                                                       |
| **Return Values** | **TRUE** for getting AppEUI successfully <br> **FALSE** for setting AppEUI failure         |


::: details Click to View Example
```c{21}

 // OTAA Application EUI MSB
  uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};

  void setup()
  {
      Serial.begin(115200);

      api.lorawan.njm.set(RAK_LORA_OTAA); // Set LoRaWan join mode to OTAA

      if(api.lorawan.appeui.set(node_app_eui, 8) == true)
          Serial.println("LoRaWan AppEUI set success");
      else
          Serial.println("LoRaWan AppEUI set fail");
  }

  void loop()
  {
      uint8_t buff[8];

      if(api.lorawan.appeui.get(buff, 8) == true) {
          Serial.print("LoRaWan AppEUI = 0x");
          for(int i = 0; i < 8; i++) {
              Serial.printf("%02X", buff[i]);
          }
          Serial.println("");
      } else {
          Serial.println("LoRaWan APPEUI get fail");
      }

      delay(1000);
  }
```
:::

#### set()

This API allows the user to set the global application identifier.

```c
api.lorawan.appeui.set(buf, len);
```

| **Function**      | `bool set(uint8_t * buf, uint32_t len)`                                                    |
| ----------------- | ------------------------------------------------------------------------------------------ |
| **Parameters**    | **`buf`**: the buffer to set AppEUI <br> **`len`**: the length of AppEUI (must be 8 bytes) |
| **Returns**       | bool                                                                                       |
| **Return Values** | **TRUE** for setting AppEUI successfully <br> **FALSE** for setting AppEUI failure         |


::: details Click to View Example
```c{11}

    // OTAA Application EUI MSB
    uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};

    void setup()
    {
        Serial.begin(115200);

        api.lorawan.njm.set(RAK_LORA_OTAA); // Set LoRaWan join mode to OTAA

        if(api.lorawan.appeui.set(node_app_eui, 8) == true)
            Serial.println("LoRaWan AppEUI set success");
        else
            Serial.println("LoRaWan AppEUI set fail");
    }

    void loop()
    {
        uint8_t buff[8];

        if(api.lorawan.appeui.get(buff, 8) == true) {
            Serial.print("LoRaWan AppEUI = 0x");
            for(int i = 0; i < 8; i++) {
                Serial.printf("%02X", buff[i]);
            }
            Serial.println("");
        } else {
            Serial.println("LoRaWan AppEUI get fail");
        }

        delay(1000);
    }
```
:::


### appkey

This API views or changes the LoRaWAN APPKEY and uses it to setup the LoRaWAN connection.

::: tip 📝 NOTE
This function can only work in OTAA mode.
:::

```c
RAKLorawan::appkey
```

#### get()

This API allows the user to get the application key.

```c
api.lorawan.appkey.get(buf, len);
```

| **Function**      | `bool get(uint8_t* buf, uint32_t len)`                                                      |
| ----------------- | ------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to get AppKey <br> **`len`**: the length of AppKey (must be 16 bytes) |
| **Returns**       | bool                                                                                        |
| **Return Values** | **TRUE** for getting AppKey successfully <br> **FALSE** for getting AppKey failure          |


::: details Click to View Example
```c{21}

// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3E};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_OTAA); // Set LoRaWan join mode to OTAA

    if(api.lorawan.appkey.set(node_app_key, 16) == true)
        Serial.println("LoRaWan AppKey set success");
    else
        Serial.println("LoRaWan AppKey set fail");
}

void loop()
{
    uint8_t buff[16];

    if(api.lorawan.appkey.get(buff, 16) == true) {
        Serial.print("LoRaWan AppKey = 0x");
        for(int i = 0; i < 16; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan AppKey get fail");
    }

    delay(1000);
}

```
:::

#### set()

This API allows the user to set the application key.

```c
api.lorawan.appkey.set(buf, len);
```

| **Function**      | `bool set(uint8_t* buf, uint32_t len)`                                                      |
| ----------------- | ------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to set AppKey <br> **`len`**: the length of AppKey (must be 16 bytes) |
| **Returns**       | bool                                                                                        |
| **Return Values** | **TRUE** for setting AppKey successfully <br> **FALSE** for setting AppKey failure          |


::: details Click to View Example
```c{11}

// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3E};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_OTAA); // Set LoRaWan join mode to OTAA

    if(api.lorawan.appkey.set(node_app_key, 16) == true)
        Serial.println("LoRaWan AppKey set success");
    else
        Serial.println("LoRaWan AppKey set fail");
}

void loop()
{
    uint8_t buff[16];

    if(api.lorawan.appkey.get(buff, 16) == true) {
        Serial.print("LoRaWan AppKey = 0x");
        for(int i = 0; i < 16; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan AppKey get fail");
    }

    delay(1000);
}

```
:::

### appskey

This API allows the user to get or set the application session key.

::: tip 📝 NOTE
This function can only work in ABP mode.
:::

```c
api.lorawan.appskey.get(buf, len);
```

#### get()

This API allows the user to get the application session key.

```c
bool get(uint8_t* buf, uint32_t len)
```

| **Function**      | `bool get(uint8_t* buf, uint32_t len)`                                                        |
| ----------------- | --------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to get AppSKey <br> **`len`**: the length of AppSKey (must be 16 bytes) |
| **Returns**       | bool                                                                                          |
| **Return Values** | **TRUE** for getting AppSKey successfully <br> **FALSE** for getting AppSKey failure          |

::: details Click to View Example
```c{21}

// ABP Application Session Key
uint8_t node_app_skey[16] = {0x25, 0xC4, 0xF1, 0xD1, 0x78, 0xC8, 0x8D, 0x01, 0xA8, 0x80, 0xC2, 0x79, 0xA7, 0x9F, 0x34, 0x3B};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_ABP); // Set LoRaWan join mode to ABP

    if(api.lorawan.appskey.set(node_app_skey, 16) == true)
        Serial.println("LoRaWan AppSKey set success");
    else
        Serial.println("LoRaWan AppSKey set fail");
}

void loop()
{
    uint8_t buff[16];

    if(api.lorawan.appskey.get(buff, 16) == true) {
        Serial.print("LoRaWan AppSKey = 0x");
        for(int i = 0; i < 16; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan AppSKey get fail");
    }

    delay(1000);
}

```
:::

#### set()

This API allows the user to set the application session key.

```c
api.lorawan.appskey.set(buf, len);
```

| **Function**      | `bool set(uint8_t* buf, uint32_t len)`                                                        |
| ----------------- | --------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to set AppSKey <br> **`len`**: the length of AppSKey (must be 16 bytes) |
| **Returns**       | bool                                                                                          |
| **Return Values** | **TRUE** for setting AppSKey successfully <br> **FALSE** for setting AppSKey failure          |


::: details Click to View Example
```c{11}

// ABP Application Session Key
uint8_t node_app_skey[16] = {0x25, 0xC4, 0xF1, 0xD1, 0x78, 0xC8, 0x8D, 0x01, 0xA8, 0x80, 0xC2, 0x79, 0xA7, 0x9F, 0x34, 0x3B};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_ABP); // Set LoRaWan join mode to ABP

    if(api.lorawan.appskey.set(node_app_skey, 16) == true)
        Serial.println("LoRaWan AppSKey set success");
    else
        Serial.println("LoRaWan AppSKey set fail");
}

void loop()
{
    uint8_t buff[16];

    if(api.lorawan.appskey.get(buff, 16) == true) {
        Serial.print("LoRaWan AppSKey = 0x");
        for(int i = 0; i < 16; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan AppSKey get fail");
    }

    delay(1000);
}

```
:::

### daddr

This API allows the user to access the device address.

::: tip 📝 NOTE
This function can only work in ABP mode.
:::

```c
RAKLorawan::daddr
```

#### get()

This API allows the user to get the device address.

```c
api.lorawan.daddr.get(buf, len);
```

| **Function**      | `bool get(uint8_t* buf, uint32_t len)`                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Parameters**    | **`buf`**: the buffer to get the device address <br> **`len`**: the length of the device address (must be 4 bytes) |
| **Returns**       | bool                                                                                                               |
| **Return Values** | **TRUE** for getting device address successfully <br> **FALSE** for getting device address failure                 |

::: details Click to View Example
```c{21}

// ABP Device Address
uint8_t node_dev_addr[4] = {0x05, 0x05, 0x06, 0x06};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_ABP); // Set LoRaWan join mode to ABP

    if(api.lorawan.daddr.set(node_dev_addr, 4) == true)
        Serial.println("LoRaWan device address set success");
    else
        Serial.println("LoRaWan device address set fail");
}

void loop()
{
    uint8_t buff[4];

    if(api.lorawan.daddr.get(buff, 4) == true) {
        Serial.print("LoRaWan device address = 0x");
        for(int i = 0; i < 4; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan device address get fail");
    }

    delay(1000);
}
```
:::

#### set()

This API allows the user to set the device address.

```c
api.lorawan.daddr.set(buf, len);
```

| **Function**      | `bool set(uint8_t* buf, uint32_t len)`                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Parameters**    | **`buf`**: the buffer to set the device address <br> **`len`**: the length of the device address (must be 4 bytes) |
| **Returns**       | bool                                                                                                               |
| **Return Values** | **TRUE** for setting device address successfully <br> **FALSE** for setting device address failure                 |


::: details Click to View Example
```c{11}

// ABP Device Address
uint8_t node_dev_addr[4] = {0x05, 0x05, 0x06, 0x06};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_ABP); // Set LoRaWan join mode to ABP

    if(api.lorawan.daddr.set(node_dev_addr, 4) == true)
        Serial.println("LoRaWan device address set success");
    else
        Serial.println("LoRaWan device address set fail");
}

void loop()
{
    uint8_t buff[4];

    if(api.lorawan.daddr.get(buff, 4) == true) {
        Serial.print("LoRaWan device address = 0x");
        for(int i = 0; i < 4; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan device address get fail");
    }

    delay(1000);
}

```
:::

### deui

This API views or changes the LoRaWAN DEUI and uses it to setup the LoRaWAN connection.

::: tip 📝 NOTE
This function can only work in OTAA mode.
:::

```c
RAKLorawan::deui
```

#### get()

This API allows the user to get the global end-device ID.

```c
api.lorawan.deui.get(buf, len);
```

| **Function**      | `bool get(uint8_t* buf, uint32_t len)`                                                                     |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to get the device EUI <br> **`len`**: the length of the device EUI (must be 8 bytes) |
| **Returns**       | bool                                                                                                       |
| **Return Values** | **TRUE** for getting device EUI successfully <br> **FALSE** for getting device EUI failure                 |


::: details Click to View Example
```c{21}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_OTAA); // Set LoRaWan join mode to OTAA

    if(api.lorawan.deui.set(node_device_eui, 8) == true)
        Serial.println("LoRaWan device EUI set success");
    else
        Serial.println("LoRaWan device EUI set fail");
}

void loop()
{
    uint8_t buff[8];

    if(api.lorawan.deui.get(buff, 8) == true) {
        Serial.print("LoRaWan device EUI = 0x");
        for(int i = 0; i < 8; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan device EUI get fail");
    }

    delay(1000);
}
```
:::

#### set()

This API allows the user to set the global end-device ID.

```c
api.lorawan.deui.set(buf, len);
```

| **Function**      | `bool set(uint8_t* buf, uint32_t len)`                                                                     |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to set the device EUI <br> **`len`**: the length of the device EUI (must be 8 bytes) |
| **Returns**       | bool                                                                                                       |
| **Return Values** | **TRUE** for setting device EUI successfully <br> **FALSE** for setting device EUI failure                 |


::: details Click to View Example
```c{11}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_OTAA); // Set LoRaWan join mode to OTAA

    if(api.lorawan.deui.set(node_device_eui, 8) == true)
        Serial.println("LoRaWan device EUI set success");
    else
        Serial.println("LoRaWan device EUI set fail");
}

void loop()
{
    uint8_t buff[8];

    if(api.lorawan.deui.get(buff, 8) == true) {
        Serial.print("LoRaWan device EUI = 0x");
        for(int i = 0; i < 8; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan device EUI get fail");
    }

    delay(1000);
}

```
:::

### netid

This API allows the user to access the network identifier (NetID).

```c
RAKLorawan::netid
```

#### get()

This API allows the user to get the network identifier (NetID).

```c
api.lorawan.netid.get(buf, len);
```

| **Function**      | `bool get(uint8_t* buf, uint32_t len)`                                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **Parameters**    | **`buf`**: the buffer to get the network identifier (NetID) <br> **`len`**: the length of the network identifier (NetID) (must be 3 bytes) |
| **Returns**       | bool                                                                                                                                       |
| **Return Values** | **TRUE** for getting the network identifier (NetID) successfully <br> **FALSE** for getting the network identifier (NetID) failure         |

::: tip 📝 NOTE
Even though the length of network identifier(NetID) is 3 bytes, you should give 4-byte buffer for natural alignment.
:::


::: details Click to View Example
```c{34}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t buff[4];

    if(api.lorawan.netid.get(buff, 4) == true) {
        Serial.print("LoRaWan network identifier(NetID) = 0x");
        for(int i = 0; i < 3; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan network identifier(NetID) get fail");
    }

    delay(1000);
}
```
:::

### nwkskey

This API allows the user to get or set the network session key.

::: tip 📝 NOTE
This function can only work in ABP mode.
:::

```c
RAKLorawan::nwkskey
```

#### get()

This API allows the user to get the network session key.

```c
api.lorawan.nwkskey.get(buf, len);
```

| **Function**      | `bool get(uint8_t* buf, uint32_t len)`                                                                                        |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **`buf`**: the buffer to get the network session key <br> **`len`**: the length of the network session key (must be 16 bytes) |
| **Returns**       | bool                                                                                                                          |
| **Return Values** | **TRUE** for getting the network session key successfully <br> **FALSE** for getting the network session key failure          |


::: details Click to View Example
```c{21}

// ABP Network Session Key
uint8_t node_nwk_skey[16] = {0xD6, 0x03, 0x37, 0xAC, 0x97, 0x4C, 0x43, 0x2F, 0xF3, 0x7A, 0xF9, 0xA7, 0x9B, 0xE8, 0x50, 0xF7};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_ABP); // Set LoRaWan join mode to ABP

    if(api.lorawan.nwkskey.set(node_nwk_skey, 16) == true)
        Serial.println("LoRaWan network session key set success");
    else
        Serial.println("LoRaWan network session key set fail");
}

void loop()
{
    uint8_t buff[16];

    if(api.lorawan.nwkskey.get(buff, 16) == true) {
        Serial.print("LoRaWan network session key = 0x");
        for(int i = 0; i < 16; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan network session key get fail");
    }

    delay(1000);
}
```
:::

#### set()

This API allows the user to set the network session key.

```c
api.lorawan.nwkskey.set(buf, len);
```

| **Function**   | `bool set(uint8_t* buf, uint32_t len)`                                                                                        |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Parameters** | **`buf`**: the buffer to set the network session key <br> **`len`**: the length of the network session key (must be 16 bytes) |
| **Returns**    | **TRUE** for setting the network session key successfully <br> **FALSE** for setting the network session key failure          |


::: details Click to View Example
```c{11}

// ABP Network Session Key
uint8_t node_nwk_skey[16] = {0xD6, 0x03, 0x37, 0xAC, 0x97, 0x4C, 0x43, 0x2F, 0xF3, 0x7A, 0xF9, 0xA7, 0x9B, 0xE8, 0x50, 0xF7};

void setup()
{
    Serial.begin(115200);

    api.lorawan.njm.set(RAK_LORA_ABP); // Set LoRaWan join mode to ABP

    if(api.lorawan.nwkskey.set(node_nwk_skey, 16) == true)
        Serial.println("LoRaWan network session key set success");
    else
        Serial.println("LoRaWan network session key set fail");
}

void loop()
{
    uint8_t buff[16];

    if(api.lorawan.nwkskey.get(buff, 16) == true) {
        Serial.print("LoRaWan network session key = 0x");
        for(int i = 0; i < 16; i++) {
            Serial.printf("%02X", buff[i]);
        }
        Serial.println("");
    } else {
        Serial.println("LoRaWan network session key get fail");
    }

    delay(1000);
}

```
:::


## Joining and Sending Data on LoRa Network


### rety

This API gets or sets the times of retransmission of Confirm packet data.

```c
RAKLorawan::rety
```

#### get()

This API gets the times of retransmission of Confirm packet data.


```c
api.lorawan.rety.get();
```


| **Function** | `uint8_t get()`                    |
| ------------ | ---------------------------------- |
| **Returns**  | the retry times for retransmission |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the times of retransmission %s\n\r", api.lorawan.rety.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The time of retransmission = %d\n\r", api.lorawan.rety.get());

    delay(1000);
}
```
:::


#### set()


This API sets the times of retransmission of Confirm packet data.

```c
api.lorawan.rety.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                              |
| ----------------- | -------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the retry times for retransmission                                         |
| **Returns**       | bool                                                                                   |
| **Return Values** | **TRUE** for setting retry time success <br> **FALSE** for setting retry times failure |


::: tip 📝 NOTE
Can only input 0 ~ 7 times.
:::


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the times of retransmission %s\n\r", api.lorawan.rety.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("The times of retransmission = %d\n\r", api.lorawan.rety.get());

    delay(1000);
}
```
:::

### cfm

This API allows the user to access the notification on received data coming from the network.

```c
RAKLorawan::cfm
```

#### get()

This API allows the user to get the notification on received data coming from the network.

```c
api.lorawan.cfm.get();
```

| **Function**      | `bool get()`                                                                                        |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** - LoRaWAN uplink is not on confirm mode <br> **FALSE** - LoRaWAN uplink is on confirm mode |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set confirm mode status %s\n\r", api.lorawan.cfm.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Packet is %s\n\r", api.lorawan.cfm.get() ? "CONFIRMED" : "UNCONFIRMED");

    delay(1000);
}

```
:::

#### set()

This API allows the user to set the notification on received data coming from the network.

```c
api.lorawan.cfm.set(value);
```

| **Function**      | `bool set(bool value)`                                                                    |
| ----------------- | ----------------------------------------------------------------------------------------- |
| **Parameters**    | **value**: the mode of confirm mode to set                                                |
| **Returns**       | bool                                                                                      |
| **Return Values** | **TRUE** for setting confirm mode success <br> **FALSE** for setting confirm mode failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set confirm mode status %s\n\r", api.lorawan.cfm.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Packet is %s\n\r", api.lorawan.cfm.get() ? "CONFIRMED" : "UNCONFIRMED");

    delay(1000);
}

```
:::


### cfs

```c
RAKLorawan::cfs
```

#### get()

This API allows the user to access the status of the last **SEND** command.

```c
api.lorawan.cfs.get();
```

| **Function** | `bool get()`                                               |
| ------------ | ---------------------------------------------------------- |
| **Returns**  | **TRUE**: Confirm success <br>  **FALSE**: Confirm failure |


::: tip 📝 NOTE
This API can only work when confirm mode is on.
:::


::: details Click to View Example
```c{35}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
        Serial.printf("Send confirm %s\r\n", api.lorawan.cfs.get() ? "Success" : "Fail");

    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}

```
:::


### njm

```c
RAKLorawan::njm
```

This API allows the user to access the network join mode.


#### get()

This API allows the user to get the network join mode.

```c
api.lorawan.njm.get();
```

| **Function**      | `bool get()`                       |
| ----------------- | ---------------------------------- |
| **Returns**       | bool                               |
| **Return Values** | **TRUE**: OTAA <br> **FALSE**: ABP |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set network join mode %s\n\r", api.lorawan.njm.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network join mode is %s\n\r", api.lorawan.njm.get() ? "OTAA" : "ABP");

    delay(1000);
}

```
:::


#### set()

This API allows the user to set the network join mode.

```c
api.lorawan.njm.set(value);
```

| **Function**      | `bool set(bool value)`                                                                              |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value**: the mode of network join mode <br> **ABP** - 0 <br> **OTAA** - 1                         |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting network join mode success <br> **FALSE** for setting network join mode failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set network join mode %s\n\r", api.lorawan.njm.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network join mode is %s\n\r", api.lorawan.njm.get() ? "OTAA" : "ABP");

    delay(1000);
}
```
:::


### njs

This API allows the user to access the current status of the LoRa link.

```c
RAKLorawan::njs
```

#### get()

This API allows the user to get the current status of the LoRa link.

```c
api.lorawan.njs.get();
```

| **Function**      | `bool get()`                                            |
| ----------------- | ------------------------------------------------------- |
| **Returns**       | bool                                                    |
| **Return Values** | **TRUE**: Network join <br> **FALSE**: Network not join |


::: details Click to View Example
```c{22}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
}
```
:::


### join()

This API does a join request to the network.

```c
api.lorawan.join();
api.lorawan.join(join_start, auto_join, auto_join_period, auto_join_cnt);
```

| **Function**      | `bool join()`                                              |
| ----------------- | ---------------------------------------------------------- |
| **Returns**       | bool                                                       |
| **Return Values** | **TRUE** for join request started  <br> **FALSE** for join request failed |

| **Function**      | `bool join()`                                              |
| ----------------- | ---------------------------------------------------------- |
| **Parameters**    | bool join_start <br> manually join network <br>  - 0 means stop to join network <br>  - 1 means start to join network
| **Parameters**    | bool auto_join <br> automatically join network <br> - 0 means stop automatically joining network <br> - 1 means start automatically joining network.
| **Parameters**    | int auto_join_period <br> the delay betweeen join attemptS. The accepted values are 7 to 255 (in seconds). .
| **Parameters**    | int auto_join_cnt <br> the maximum number of join attempts. The accepted values are 0 to 255 (attempts).
| **Returns**       | bool                                                       |
| **Return Values** | **TRUE** for join request started  <br> **FALSE** for join request failed |


::: details Click to View Example
```c{25}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
}
```
:::

:::tip 📝 NOTE:
This is an asynchronous command. A result of TRUE means that the device is joining. The completion of the join process can be verified with the `api.lorawan.njs.get()` command.

Parameters of `api.lorawan.join()` command are optional. You can use `api.lorawan.join()` directly to join the LoRaWAN network. If no parameters are configured, the device will use the default values.

The result of the join process is reported in the `JoinCallback`. You can register a join callback handler with `api.lorawan.registerJoinCallback(service_lora_join_cb callback) `
:::

### send()

This API provides the way to send data on a dedicated port number.

```c
api.lorawan.send(length, payload, fport);
```

```c
api.lorawan.send(length, payload, fport, confirm);
```

```c
api.lorawan.send(length, payload, fport, confirm, retry);
```

| **Function**      | `bool send(uint8_t length,uint8_t * payload, uint8_t fport, bool confirm = true, uint8_t retry)`                                                                                                                                                                                                     |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **length** - the length of the payload <br> **payload** - the data to uplink <br> **fport** - allow 1 ~ 223 <br> **confirm** - Override cfm setting to get confirm message from gateway (optional) <br> **retry** - Override retry setting to retry if sending failed (optional) |
| **Returns**       | bool                                                                                                                                                                                                                                                                                                 |
| **Return Values** | **TRUE** for start sending uplink success <br> **FALSE** for start sending uplink failed              |


::: details Click to View Example
```c{34}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}
```
:::

:::tip 📝 NOTE:
This is an asynchronous command. A result of TRUE means that the device is starting to send the payload. The completion of the send process is reported in the `SendCallback`. You can register a send callback handler with `api.lorawan.registerSendCallback(service_lora_send_cb callback) `
:::

### lpsend()

This API provides a way to send long packet (1024 bytes) text data.


```c
api.lorawan.lpsend(port, ack, payload, length);
```


| **Function**      | `bool lpsend(uint8_t port, bool ack, uint8_t * payload, int length)`                                                                                                                                  |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **port** - application port to be transmitted  <br> **ack** - indicate this is a confirmed message or not  <br>  **payload**	the data you want to send   <br>  **length** - the length of the payload |
| **Returns**       | bool                                                                                                                                                                                                  |
| **Return Values** | **TRUE** for sending data success <br> **FALSE** for sending data failure                                                                                                                             |


**Example:**
::: details Click to View Example
```c

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "12345678901234567890";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}

```
:::

:::tip 📝 NOTE:
This is an asynchronous command. A result of TRUE means that the device is starting to send the payload. The completion of the send process is reported in the `SendCallback`. You can register a send callback handler with `api.lorawan.registerSendCallback(service_lora_send_cb callback) `
:::

### registerRecvCallback()

This API registers a callback function, so that application can be notified on receiving LoRaWAN data.


```c
api.lorawan.registerRecvCallback(service_lora_recv_cb callback);
```



| **Function**      | `bool registerRecvCallback(service_lora_recv_cb callback)`                                          |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** callback function                                                                           |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |


::: details Click to View Example
```c{36}

void recv_cb(SERVICE_LORA_RECEIVE_T *data) {
  Serial.println("Something received!");
  for (int i = 0 ; i < data->BufferSize ; i++) {
    Serial.printf("%x", data->Buffer[i]);
  }
  Serial.print("\r\n");
}

void join_cb(int32_t status) {
  Serial.printf("Join status: %d\r\n", status);
}

void send_cb(int32_t status) {
  Serial.printf("Send status: %d\r\n", status);
}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();
    api.lorawan.registerRecvCallback(recv_cb);
    api.lorawan.registerJoinCallback(join_cb);
    api.lorawan.registerSendCallback(send_cb);

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}
```
:::


### registerJoinCallback()


This API registers a callback function, so that application can be notified when joining process is done.

```c
api.lorawan.registerJoinCallback(service_lora_join_cb callback);
```


| **Function**      | `bool registerJoinCallback(service_lora_join_cb callback)`                                          |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** callback function                                                                           |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |


::: details Click to View Example
```c{36}
void recv_cb(SERVICE_LORA_RECEIVE_T *data) {
  Serial.println("Something received!");
  for (int i = 0 ; i < data->BufferSize ; i++) {
    Serial.printf("%x", data->Buffer[i]);
  }
  Serial.print("\r\n");
}

void join_cb(int32_t status) {
  Serial.printf("Join status: %d\r\n", status);
}

void send_cb(int32_t status) {
  Serial.printf("Send status: %d\r\n", status);
}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();
    api.lorawan.registerRecvCallback(recv_cb);
    api.lorawan.registerJoinCallback(join_cb);
    api.lorawan.registerSendCallback(send_cb);

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}
```
:::


### registerSendCallback()

This API registers a callback function, so that application can be notified when uplink process is done.

```c
api.lorawan.registerSendCallback(service_lora_send_cb callback);
```


| **Function**      | `bool registerSendCallback(service_lora_send_cb callback)`                                          |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** callback function                                                                           |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |


::: details Click to View Example
```c{38}

void recv_cb(SERVICE_LORA_RECEIVE_T *data) {
  Serial.println("Something received!");
  for (int i = 0 ; i < data->BufferSize ; i++) {
    Serial.printf("%x", data->Buffer[i]);
  }
  Serial.print("\r\n");
}

void join_cb(int32_t status) {
  Serial.printf("Join status: %d\r\n", status);
}

void send_cb(int32_t status) {
  Serial.printf("Send status: %d\r\n", status);
}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();
    api.lorawan.registerRecvCallback(recv_cb);
    api.lorawan.registerJoinCallback(join_cb);
    api.lorawan.registerSendCallback(send_cb);

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}
```
:::

### registerLinkCheckCallback()

This API registers a callback function, so that application can be notified when linkcheck result is available.

```c
api.lorawan.registerLinkCheckCallback(service_lora_linkcheck_cb callback);
```


| **Function**      | `bool registerLinkCheckCallback(service_lora_linkcheck_cb  callback)`                                          |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** callback function                                                                           |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |


::: details Click to View Example
```c{38}
void linkcheck_cb(SERVICE_LORA_LINKCHECK_T *data) {
  Serial.println("linkcheck_cb");
   Serial.printf("State:%u\r\n",data->State);
   Serial.printf("DemodMargin:%u\r\n",data->DemodMargin);
   Serial.printf("NbGateways:%u\r\n",data->NbGateways);
   Serial.printf("rssi:%u\r\n",data->Rssi);
   Serial.printf("snr:%u\r\n",data->Snr);
}
void recv_cb(SERVICE_LORA_RECEIVE_T *data) {
  Serial.println("Something received!");
  for (int i = 0 ; i < data->BufferSize ; i++) {
    Serial.printf("%x", data->Buffer[i]);
  }
  Serial.print("\r\n");
}

void join_cb(int32_t status) {
  Serial.printf("Join status: %d\r\n", status);
}
void send_cb(int32_t status) {
  Serial.printf("Send status: %d\r\n", status);
}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();
    api.lorawan.registerRecvCallback(recv_cb);
    api.lorawan.registerJoinCallback(join_cb);
    api.lorawan.registerSendCallback(send_cb);
    api.lorawan.registerLinkCheckCallback(linkcheck_cb);

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}
void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    } else {
        Serial.println("Send fail");

    }

    delay(5000);
}
```
:::

### registerTimereqCallback()

This API registers a callback function, so that application can be notified when time request result is available.

```c
api.lorawan.registerTimereqCallback(service_lora_timereq_cb callback) ;
```


| **Function**      | `bool registerTimereqCallback(service_lora_timereq_cb callback)`                                          |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** callback function                                                                           |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |


::: details Click to View Example
```c{38}
bool f_synctime = true;

void timereq_cb(uint32_t status) {
  Serial.println("Timereq_cb");
  if (status == GET_DEVICE_TIME_OK) {
    Serial.println("Get device time success");
    f_synctime = false;
  }
  else if (status == GET_DEVICE_TIME_FAIL) {
    Serial.println("Get device time fail");
    f_synctime = true;
  }
}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
  Serial.begin(115200);

  api.lorawan.appeui.set(node_app_eui, 8);
  api.lorawan.appkey.set(node_app_key, 16);
  api.lorawan.deui.set(node_device_eui, 8);

  api.lorawan.band.set(4);
  api.lorawan.njm.set(1);
  api.lorawan.join();
  api.lorawan.registerTimereqCallback(timereq_cb);

  //wait for Join success
  while (api.lorawan.njs.get() == 0)
  {
    Serial.print("Waiting for Lorawan join...");
    api.lorawan.join();
    delay(10000);
  }
}

void loop()
{
  uint8_t payload[] = "example";

  if (f_synctime == true && api.lorawan.timereq.get() == 0) {
    api.lorawan.timereq.set(1);
  }

  if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
    Serial.println("Send Success");
  } else {
    Serial.println("Send fail");
  }

  delay(5000);
}
```
:::

## Class B Mode


### pgslot

This API allows the user to get or set the unicast ping slot periodicity.

```c
RAKLorawan::pgslot
```

#### get()

This API allows the user to get the unicast ping slot periodicity.

```c
api.lorawan.pgslot.get();
```

| **Function** | `uint8_t get()`           |
| ------------ | ------------------------- |
| **Returns**  | the ping slot periodicity |



::: details Click to View Example
```c{33}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.deviceClass.set(1);
    Serial.printf("Set the unicast ping slot periodicity %s\r\n", api.lorawan.pgslot.set(0) ? "Success" : "Fail");
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    Serial.printf("The unicast ping slot periodicity is %d\r\n", api.lorawan.pgslot.get());
    delay(1000);
}
```
:::

#### set()

This API allows the user to set the unicast ping slot periodicity.

```c
api.lorawan.pgslot.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                                                      |
| ----------------- | -------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the unicast ping slot periodicity                                                                  |
| **Returns**       | bool                                                                                                           |
| **Return Values** | **TRUE** for setting ping slot periodicity success  <br>   **FALSE** for setting ping slot periodicity failure |


::: details Click to View Example
```c{19}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.deviceClass.set(1);
    Serial.printf("Set the unicast ping slot periodicity %s\r\n", api.lorawan.pgslot.set(0) ? "Success" : "Fail");
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    Serial.printf("The unicast ping slot periodicity is %d\r\n", api.lorawan.pgslot.get());
    delay(1000);
}
```
:::

### bfreq

This API allows the user to access the current beacon (default broadcast) frequency.

```c
RAKLorawan::bfreq
```

#### get()

This API allows the user to access the current beacon (default broadcast) frequency.

```c
api.lorawan.bfreq.get();
```

| **Function** | `float get()`                                 |
| ------------ | --------------------------------------------- |
| **Returns**  | the current beacon frequency (Type: **long**) |


::: details Click to View Example
```c{32}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.deviceClass.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    Serial.printf("The current beacon frequency =  %.0f\r\n", api.lorawan.bfreq.get());
    delay(1000);
}
```
:::


### btime

This API allows the user to access the current beacon time

```c
RAKLorawan::btime
```

#### get()

This API allows the user to access the current beacon time.

```c
api.lorawan.btime.get()
```

| **Function** | `long get()`               |
| ------------ | -------------------------- |
| **Returns**  | the current beacon time(b) |


::: details Click to View Example
```c{32}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.deviceClass.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    Serial.printf("The current beacon time = %l\r\n", api.lorawan.btime.get());
    delay(1000);
}
```


### bgw

This API allows the user to access the gateway GPS coordinate, NetID and GwID

```c
RAKLorawan::bgw
```

#### get()

This API allows the user to access the gateway GPS coordinate, NetID, and GwID.

```c
api.lorawan.bgw.get();
```

| **Function** | `beacon_bgw_t get()` |
| ------------ | -------------------- |
| **Returns**  | `beacon_bgw_t`       |


::: details Click to View Example
```c{34}
beacon_bgw_t beaconBGW;

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
  //Serial.begin(115200);

  api.lorawan.appeui.set(node_app_eui, 8);
  api.lorawan.appkey.set(node_app_key, 16);
  api.lorawan.deui.set(node_device_eui, 8);

  api.lorawan.band.set(4);
  api.lorawan.deviceClass.set(1);
  api.lorawan.njm.set(1);
  api.lorawan.join();

  //Wait for Join success
  while (api.lorawan.njs.get() == 0)
  {
    Serial.print("Waiting for Lorawan join...");
    api.lorawan.join();
    delay(10000);
  }
}

void loop()
{
  beaconBGW = api.lorawan.bgw.get();

  Serial.printf("GPS Coordinate = %u\r\n", (unsigned int)beaconBGW.GPS_coordinate);
  Serial.printf("Latitude = %f\r\n", (float)beaconBGW.latitude*(float)90/(float)8388607);
  Serial.printf("longitude = %f\r\n", (float)beaconBGW.longitude*(float)180/(float)8388607);
  Serial.printf("Net ID = %u\r\n", (unsigned int)beaconBGW.net_ID);
  Serial.printf("Gateway ID = %u\r\n", (unsigned int)beaconBGW.gateway_ID);

  delay(1000);
}
```
:::


### ltime()

This API allows the user to access the local time in a UTC format
```c
RAKLorawan::bgw
```

#### get()

This API allows the user to get the local time in a UTC format.

```c
api.lorawan.ltime.get();
```

| **Function** | `string get()`                                  |
| ------------ | ----------------------------------------------- |
| **Returns**  | the local time in a UTC format (Type: **bool**) |


::: details Click to View Example
```c{32}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.deviceClass.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    Serial.printf("The local time(UTC) is %s\r\n", api.lorawan.ltime.get().c_str());
    delay(1000);
}
```
:::


## Information


### rssi
This API allows the user to access the RSSI on reception

```c
RAKLorawan::rssi
```

::: tip 📝 NOTE
When the connection is successful, get the RSSI of the last received packet.
:::


#### get()

This API allows the user to access the RSSI on reception.

```c
api.lorawan.rssi.get();
```

| **Function** | `int get()`                           |
| ------------ | ------------------------------------- |
| **Returns**  | the RSSI on reception (Type: **int**) |


::: details Click to View Example
```c{35}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
    Serial.printf("LoRaWan RSSI = %d\r\n", api.lorawan.rssi.get());

    } else {
        Serial.println("Send fail");
    }

    delay(5000);
}
```
:::


### snr

This API allows the user to access the SNR of the last received packet
```c
RAKLorawan::snr
```

::: tip 📝 NOTE
When the connection is successful, get the SNR of the last received packet.
:::


#### get()

This API allows the user to get the SNR of the last received packet.

```c
api.lorawan.snr.get();
```

| **Function** | `int get()`                                         |
| ------------ | --------------------------------------------------- |
| **Returns**  | the SNR of the last received packet (Type: **int**) |


::: details Click to View Example
```c{35}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
    Serial.begin(115200);

    api.lorawan.appeui.set(node_app_eui, 8);
    api.lorawan.appkey.set(node_app_key, 16);
    api.lorawan.deui.set(node_device_eui, 8);

    api.lorawan.band.set(4);
    api.lorawan.njm.set(1);
    api.lorawan.join();

    //wait for Join success
    while (api.lorawan.njs.get() == 0)
    {
      Serial.print("Waiting for Lorawan join...");
      api.lorawan.join();
      delay(10000);
    }
}

void loop()
{
    uint8_t payload[] = "example";

    if (api.lorawan.send(sizeof(payload), payload, 129, true, 1)) {
        Serial.println("Send Success");
        Serial.printf("LoRaWan SNR = %d\r\n", api.lorawan.snr.get());

    } else {
        Serial.println("Send fail");
    }

    delay(5000);
}
```
:::


### ver

This API allows the user to get the LoRaWAN version.

```c
RAKLorawan::ver
```


#### get()

This API allows the user to get the LoRaWAN version.

```c
api.lorawan.ver.get();
```

| **Function** | `string get()`                         |
| ------------ | -------------------------------------- |
| **Returns**  | the LoRaWAN version (Type: **string**) |



::: details Click to View Example
```c{8}
void setup()
{
    Serial.begin(115200);
}

void loop()
{
    Serial.printf("The LoRaWan version is %s\r\n", api.lorawan.ver.get().c_str());
    delay(1000);
}
```
:::




### arssi()

This API can access all open channel rssi.


```c
api.lorawan.arssi(chan_arssi);
```


| **Function**      | `bool arssi(RAK_LORA_chan_rssi * iterator)`                                |
| ----------------- | -------------------------------------------------------------------------- |
| **Parameters**    | **chan_arssi** - the structure array to store arssi                        |
| **Returns**       | bool                                                                       |
| **Return Values** | **TRUE** for getting arssi success <br> **Fail** for getting arssi failure |



::: details Click to View Example
```c{34}
// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x03};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3C};

void setup()
{
  Serial.begin(115200);

  api.lorawan.appeui.set(node_app_eui, 8);
  api.lorawan.appkey.set(node_app_key, 16);
  api.lorawan.deui.set(node_device_eui, 8);
  api.lorawan.band.set(4);

  api.lorawan.njm.set(1);
  api.lorawan.join();

  //Wait for Join success
  while (api.lorawan.njs.get() == 0)
  {
    Serial.print("Waiting for Lorawan join...");
    api.lorawan.join();
    delay(10000);
  }
}

void loop()
{
  RAK_LORA_chan_rssi chan_arssi;

  Serial.print("Get All open channel RSSI =");
  while (api.lorawan.arssi(&chan_arssi) == true) {
    if (chan_arssi.mask != 0) {
      Serial.printf("channel : %d,mask : %d, rssi : %d\r\n", chan_arssi.chan, chan_arssi.mask, chan_arssi.rssi);
    }
  }
  Serial.print("\r\n");

  delay(5000);
}
```
:::



## LoRaWAN Regional Commands

### mask

This API configures the channel of the device by setting the hexadecimal channel mask. The complete table for mask value can be found on [AT+MASK section](/RUI3/Serial-Operating-Modes/AT-Command-Manual/#at-mask)

:::tip 📝 NOTE
Only for US915, AU915, LA915, CN470
:::

```c
RAKLorawan::mask
```


#### get()

This API allows the user to get the channel mask, close or open the channel.

```c
api.lorawan.mask.get(buff);
```


| **Function**      | `bool get(uint16_t * buff)`                                                               |
| ----------------- | ----------------------------------------------------------------------------------------- |
| **Parameters**    | **buff** - the buffer to store channel mask                                               |
| **Returns**       | bool                                                                                      |
| **Return Values** | **TRUE** for getting channel mask success <br> **FALSE** for getting channel mask failure |


::: details Click to View Example
```c{15}
uint16_t maskBuff = 0x0003;

void setup()
{
    Serial.begin(115200);

    api.lorawan.band.set(5);
    Serial.printf("Set channel mask %s\r\n", api.lorawan.mask.set(&maskBuff) ? "Success" : "Fail");

}

void loop()
{

    Serial.printf("Get channel mask %s\r\n", api.lorawan.mask.get(&maskBuff) ? "Success" : "Fail");
    Serial.printf("Channel mask = %04X\r\n", maskBuff);
    delay(1000);
}
```
:::


#### set()

This API allows the user to set the channel mask, close or open the channel.

```c
api.lorawan.mask.set(value);
```


| **Function**      | `bool set(uint16_t * value)`                                                                |
| ----------------- | ------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the buffer to set the channel mask                                              |
| **Returns**       | bool                                                                                        |
| **Return Values** | **TRUE** for setting channel mask success <br>   **FALSE** for setting channel mask failure |


::: details Click to View Example
```c{8}
uint16_t maskBuff = 0x0003;

void setup()
{
    Serial.begin(115200);

    api.lorawan.band.set(5);
    Serial.printf("Set channel mask %s\r\n", api.lorawan.mask.set(&maskBuff) ? "Success" : "Fail");

}

void loop()
{

    Serial.printf("Get channel mask %s\r\n", api.lorawan.mask.get(&maskBuff) ? "Success" : "Fail");
    Serial.printf("Channel mask = %04X\r\n", maskBuff);
    delay(1000);
}

```
:::

The table below shows the attached list on setting the channel mask.

<table style="text-align: center">
<thead>
  <tr>
    <th>Sub-Band</th>
    <th>Channels</th>
    <th>16bits</th>
    <th>US915</th>
    <th>AU915</th>
    <th>LA915</th>
    <th>CN470</th>
  </tr>
</thead>
<tbody>
        <tr>
            <td>ALL</td>
            <td>0000</td>
            <td>0000000000000000</td>
            <td>All Channels</td>
            <td>All Channels</td>
            <td>All Channels</td>
            <td>All Channels</td>
        </tr>
        <tr>
            <td>1</td>
            <td>0001</td>
            <td>0000000000000001</td>
            <td>0-7, 64</td>
            <td>0-7, 64</td>
            <td>0-7, 64</td>
            <td>0-7</td>
        </tr>
        <tr>
           <td>2</td>
            <td>0002</td>
            <td>0000000000000010</td>
            <td>8-15, 65</td>
            <td>8-15, 65</td>
            <td>8-15, 65</td>
            <td>8-15</td>
        </tr>
        <tr>
           <td>3</td>
            <td>0004</td>
            <td>0000000000000100</td>
            <td>16-23, 66</td>
            <td>16-23, 66</td>
            <td>16-23, 66</td>
            <td>16-23</td>
        </tr>
        <tr>
           <td>4</td>
            <td>0008</td>
            <td>0000000000001000</td>
            <td>24-31, 67</td>
            <td>24-31, 67</td>
            <td>24-31, 67</td>
            <td>24-31</td>
        </tr>
        <tr>
           <td>5</td>
            <td>0010</td>
            <td>0000000000010000</td>
            <td>32-39, 68</td>
            <td>32-39, 68</td>
            <td>32-39, 68</td>
            <td>32-39</td>
        </tr>
        <tr>
           <td>6</td>
            <td>0020</td>
            <td>0000000000100000</td>
            <td>40-47, 69</td>
            <td>40-47, 69</td>
            <td>40-47, 69</td>
            <td>40-47</td>
        </tr>
        <tr>
           <td>7</td>
            <td>0040</td>
            <td>0000000001000000</td>
            <td>48-55, 70</td>
            <td>48-55, 70</td>
            <td>48-55, 70</td>
            <td>48-55</td>
        </tr>
        <tr>
           <td>8</td>
            <td>0080</td>
            <td>0000000010000000</td>
            <td>56-63, 71</td>
            <td>56-63, 71</td>
            <td>56-63, 71</td>
            <td>56-63</td>
        </tr>
        <tr>
           <td>9</td>
            <td>0100</td>
            <td>0000000100000000</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>64-71</td>
        </tr>
        <tr>
           <td>10</td>
            <td>0200</td>
            <td>0000001000000000</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>72-79</td>
        </tr>
        <tr>
           <td>11</td>
            <td>0400</td>
            <td>0000010000000000</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>80-87</td>
        </tr>
        <tr>
           <td>12</td>
            <td>0800</td>
            <td>0000100000000000</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>88-95</td>
        </tr>
</tbody>
</table>


### band

This API set number corresponding to active regions.


```c
RAKLorawan::band
```

::: tip 📝 NOTE

0: EU433
1: CN470
2: RU864
3: IN865
4: EU868
5: US915
6: AU915
7: KR920
8: AS923-1
9: AS923-2
10: AS923-3
11: AS923-4
12: LA915

:::

::: tip 📝 NOTE

If you use US915, channel 8-15 is commonly used on 8-ch Gateway/LoRaWAN network setup. You can use mask API to enable only these channels.
```c
uint16_t maskBuff = 0x0002;
Serial.printf("Set channel mask %s\r\n", api.lorawan.mask.set(&maskBuff) ? "Success" : "Fail");
```
:::

#### get()

This API gets the number corresponding to active regions.


```c
api.lorawan.band.get();
```


| **Function**      | `int32_t get()`                                                                                                                                                                                                                                                |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Returns**       | the active region                                                                                                                                                                                                                                              |
| **Return Values** | **0** - EU433  <br>  **1** - CN470 <br> **2** - RU864 <br> **3**	- IN865 <br> **4** - EU868 <br> **5**	- US915 <br> **6** - AU915 <br> **7** - KR920 <br> **8** - AS923-1 <br> **9** - AS923-2 <br> **10** - AS923-3 <br> **11** - AS923-4 <br> **12** - LA915 |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set LoRa region %s\r\n", api.lorawan.band.set(4) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("LoRa region = %d\r\n", api.lorawan.band.get());

    delay(1000);
}
```
:::

##### set()


This API set number corresponding to active regions.


```c
api.lorawan.band.set(value);
```


| **Function**      | `bool set(uint8_t value)`                                                                    |
| ----------------- | -------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the active region to set                                                         |
| **Returns**       | bool                                                                                         |
| **Return Values** | **TRUE** for setting active region success <br>  **FALSE** for setting active region failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set LoRa region %s\r\n", api.lorawan.band.set(4) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("LoRa region = %d\r\n", api.lorawan.band.get());

    delay(1000);
}

```
:::



## Multicast Group Command

### addmulc()

This API adds a new multicast group configure multicast parameters.

```c
api.lorawan.addmulc(session);
```


| **Function**      | `bool addmulc(RAK_LORA_McSession session)`                                                     |
| ----------------- | ---------------------------------------------------------------------------------------------- |
| **Parameters**    | **session** - The structure of session                                                         |
| **Returns**       | bool                                                                                           |
| **Return Values** | **TRUE**  for adding multicast group success <br> **FALSE** for adding multicast group failure |



::: details Click to View Example
```c{54}
void setup()
{
  Serial.begin(115200);

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x88};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x0E};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3E};



//LoRaWan Multicast Session

uint8_t node_mc_address[4] = {0x01, 0x02, 0x03, 0x04};
uint8_t node_mc_AppSKey[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t node_mc_NwkSKey[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};

RAK_LORA_McSession session = {
    .McDevclass = 2,
    .McAddress = node_mc_address[0]<<24 | node_mc_address[1]<<16 | node_mc_address[2]<<8 | node_mc_address[3],
    .McFrequency = 869525000,
    .McDatarate = 0,
    .McPeriodicity = 0,
    .McGroupID = 2,
    .entry = 0,
};
  memcpy(session.McAppSKey, node_mc_AppSKey, 16);
  memcpy(session.McNwkSKey, node_mc_NwkSKey, 16);

  api.lorawan.appeui.set(node_app_eui, 8);
  api.lorawan.appkey.set(node_app_key, 16);
  api.lorawan.deui.set(node_device_eui, 8);

  api.lorawan.band.set(4);
  api.lorawan.njm.set(1);
  api.lorawan.deviceClass.set(2);
  api.lorawan.join();

  //Wait for Join success
  while (api.lorawan.njs.get() == 0)
  {
    Serial.print("Waiting for Lorawan join...");
    api.lorawan.join();
    delay(10000);
  }

  api.lorawan.adr.set(true);
  api.lorawan.rety.set(1);
  api.lorawan.cfm.set(1);

  //LoRaWAN Multicast Setting
  if(api.lorawan.addmulc(session) == true) {
    Serial.println("Add Multicast Success");
  } else {
    Serial.println("Add Multicast Fail");
  }

}

void loop()
{

}

```
:::


### rmvmulc()

This API allows the removal of a configured multicast group.

```c
api.lorawan.rmvmulc(devAddr);
```


| **Function**      | `bool rmvmulc(uint32_t devAddr)`                                  |
| ----------------- | ----------------------------------------------------------------- |
| **Parameters**    | **devAddr** - the address to remove a multicast group             |
| **Returns**       | bool                                                              |
| **Return Values** | **TRUE** for removing success <br> **FALSE** for removing failure |


::: details Click to View Example
```c{64}

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x88};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x0E};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3E};

//LoRaWan Multicast Session
uint8_t node_mc_address[4] = {0x01, 0x02, 0x03, 0x04};
uint8_t node_mc_AppSKey[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t node_mc_NwkSKey[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};


void setup()
{
  Serial.begin(115200);

  RAK_LORA_McSession session = {
      .McDevclass = 2,
      .McAddress = node_mc_address[0]<<24 | node_mc_address[1]<<16 | node_mc_address[2]<<8 | node_mc_address[3],
      .McFrequency = 869525000,
      .McDatarate = 0,
      .McPeriodicity = 0,
      .McGroupID = 2,
      .entry = 0,
  };
  memcpy(session.McAppSKey, node_mc_AppSKey, 16);
  memcpy(session.McNwkSKey, node_mc_NwkSKey, 16);

  api.lorawan.appeui.set(node_app_eui, 8);
  api.lorawan.appkey.set(node_app_key, 16);
  api.lorawan.deui.set(node_device_eui, 8);

  api.lorawan.band.set(4);
  api.lorawan.njm.set(1);
  api.lorawan.deviceClass.set(2);
  api.lorawan.join();

  //Wait for Join success
  while (api.lorawan.njs.get() == 0)
  {
    Serial.print("Waiting for Lorawan join...");
    api.lorawan.join();
    delay(10000);
  }

  api.lorawan.adr.set(true);
  api.lorawan.rety.set(1);
  api.lorawan.cfm.set(1);

  //LoRaWAN Multicast Setting
  if(api.lorawan.addmulc(session) == true) {
    Serial.println("Add Multicast Success");
  } else {
    Serial.println("Add Multicast Fail");
  }

}

void loop()
{
  if(millis() > 100000) {
     Serial.printf("Remove a multicast group %s\r\n", api.lorawan.rmvmulc(node_mc_address[0]<<24 | node_mc_address[1]<<16 | node_mc_address[2]<<8 | node_mc_address[3]));
   }
}

```
:::


### lstmulc()


This command can view current configured multicast group information.

```c
api.lorawan.lstmulc(&multicast_list);
```

| **Function**      | `bool lstmulc(RAK_LORA_McSession * iterator)`                                            |
| ----------------- | ---------------------------------------------------------------------------------------- |
| **Parameters**    | **multicast_list** - a RAK_LORA_McSession variable                                       |
| **Returns**       | bool                                                                                     |
| **Return Values** | **TRUE** for getting multicast list success <br> **FALSE** for getting multicast failure |


::: details Click to View Example
```c{67}
void setup()
{
  Serial.begin(115200);

// OTAA Device EUI MSB
uint8_t node_device_eui[8] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x88};
// OTAA Application EUI MSB
uint8_t node_app_eui[8] = {0x0E, 0x0D, 0x0D, 0x01, 0x0E, 0x01, 0x02, 0x0E};
// OTAA Application Key MSB
uint8_t node_app_key[16] = {0x2B, 0x7E, 0x15, 0x16, 0x28, 0xAE, 0xD2, 0xA6, 0xAB, 0xF7, 0x15, 0x88, 0x09, 0xCF, 0x4F, 0x3E};



//LoRaWan Multicast Session

uint8_t node_mc_address[4] = {0x01, 0x02, 0x03, 0x04};
uint8_t node_mc_AppSKey[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t node_mc_NwkSKey[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};

RAK_LORA_McSession session = {
    .McDevclass = 2,
    .McAddress = node_mc_address[0]<<24 | node_mc_address[1]<<16 | node_mc_address[2]<<8 | node_mc_address[3],
    .McFrequency = 869525000,
    .McDatarate = 0,
    .McPeriodicity = 0,
    .McGroupID = 2,
    .entry = 0,
};
  memcpy(session.McAppSKey, node_mc_AppSKey, 16);
  memcpy(session.McNwkSKey, node_mc_NwkSKey, 16);

  api.lorawan.appeui.set(node_app_eui, 8);
  api.lorawan.appkey.set(node_app_key, 16);
  api.lorawan.deui.set(node_device_eui, 8);

  api.lorawan.band.set(4);
  api.lorawan.njm.set(1);
  api.lorawan.deviceClass.set(2);
  api.lorawan.join();

  //Wait for Join success
  while (api.lorawan.njs.get() == 0)
  {
    Serial.print("Waiting for Lorawan join...");
    api.lorawan.join();
    delay(10000);
  }

  api.lorawan.adr.set(true);
  api.lorawan.rety.set(1);
  api.lorawan.cfm.set(1);

  //LoRaWAN Multicast Setting
  if(api.lorawan.addmulc(session) == true) {
    Serial.println("Add Multicast Success");
  } else {
    Serial.println("Add Multicast Fail");
  }

}

void loop()
{
  RAK_LORA_McSession multicast_list;

  Serial.println("Get all multicast groups");
  while (api.lorawan.lstmulc(&multicast_list) == true) {
    if (multicast_list.McDevclass != 0) {
      Serial.printf("Device class = %d\r\n", multicast_list.McDevclass);
      Serial.printf("Device address = %08X\r\n", multicast_list.McAddress);

      Serial.print("Multicast AppSKey = 0x");
      for (int i=0; i<16; i++) {
        Serial.printf("%02X", multicast_list.McAppSKey[i]);
      }
      Serial.println("");

      Serial.print("Multicast NwkSKey = 0x");
      for (int i=0; i<16; i++) {
        Serial.printf("%02X", multicast_list.McNwkSKey[i]);
      }
      Serial.println("");

      Serial.printf("Frequency = %d\r\n", multicast_list.McFrequency);
      Serial.printf("Data rate = %d\r\n", multicast_list.McDatarate);
      Serial.printf("Periodicity = %d\r\n", multicast_list.McPeriodicity);
      Serial.printf("Group ID = %d\r\n", multicast_list.McGroupID);
      Serial.printf("Entry = %d\r\n", multicast_list.entry);
    }
  }

  delay(5000);

}


```
:::


## P2P Instructions

### nwm

Switch to point-to-point mode

```c
RAKLora::nwm
```

#### get()

This API gets the network working mode (0 = P2P, 1 = LoRaWAN, 2 = FSK).

```c
api.lora.nwm.get();
```


| **Function**      | `int get()`                                                      |
| ----------------- | ---------------------------------------------------------------- |
| **Returns**       | the network working mode                                         |
| **Return Values** | **0** - P2P mode <br> **1** - LoRaWAN mode <br> **2** - FSK mode |



::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the network working mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network working mode = %s\r\n", api.lora.nwm.get() ? "LoRaWan" : "P2P");

    delay(1000);
}
```
:::

#### set()

This API sets the network working mode to P2P.

```c
api.lora.nwm.set(value);
```

| **Function**      | `bool set()	`                                                                                 |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| **Returns**       | bool                                                                                                       |
| **Return Values** | **TRUE** for setting network working mode success <br>  **FALSE** for setting network working mode failure |

::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);

    Serial.printf("Set the network working mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("Network working mode = %s\r\n", api.lora.nwm.get() ? "LoRaWan" : "P2P");

    delay(1000);
}

```
:::


### pfreq

This API provides configuration frequency for the P2P mode.


```c
RAKLora::pfreq
```


#### get()

This API gets the P2P frequency.

```c
api.lora.pfreq.get();
```


| **Function** | `uint32_t get()`           |
| ------------ | -------------------------- |
| **Returns**  | The frequency for P2P mode |

::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode frequency = %d\r\n", api.lora.pfreq.get());

    delay(1000);
}
```
:::


#### set()


This API sets the P2P frequency.


```c
api.lora.pfreq.set(value);
```

| **Function**      | `bool set(uint32_t value)`                                                           |
| ----------------- | ------------------------------------------------------------------------------------ |
| **Parameters**    | **value** - the frequency for P2P mode                                               |
| **Returns**       | bool                                                                                 |
| **Return Values** | **TRUE** for setting frequency success <br>  **FALSE** for setting frequency failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode frequency = %d\r\n", api.lora.pfreq.get());

    delay(1000);
}
```
:::


### psf

This API provides a configuration Spreading Factor for the P2P mode.

```c
RAKLora::psf
```

#### get()

This API gets P2P Spreading Factor (6, 7, 8, 9, 10, 11, 12).

```c
api.lora.psf.get();
```

| **Function** | `uint8_t get()`          |
| ------------ | ------------------------ |
| **Returns**  | The P2P spreading factor |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode spreading factor = %d\r\n", api.lora.psf.get());

    delay(1000);
}
```
:::


#### set()

This API sets P2P Spreading Factor (6,7, 8, 9, 10, 11, 12).

```c
api.lora.psf.set(value);
```



| **Function**      | `bool set(uint8_t value)`                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the P2P spreading factor                                                                       |
| **Returns**       | bool                                                                                                       |
| **Return Values** | **TRUE** for setting P2P spreading factor success <br>  **FALSE** for setting P2P spreading factor failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode spreading factor = %d\r\n", api.lora.psf.get());

    delay(1000);
}
```
:::


### pbw

This API provides configuration bandwidth for the P2P mode.


```c
RAKLora::pbw
```

#### get()


This API gets P2P bandwidth in kHz (0 = 125, 1 = 250, 2 = 500, 3 = 7.8, 4 = 10.4, 5 = 15.63, 6 = 20.83, 7 = 31.25, 8 = 41.67, 9 = 62.5).

```c
api.lora.pbw.get();
```


| **Function** | `uint32_t get()`  |
| ------------ | ----------------- |
| **Returns**  | The P2P bandwidth |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode bandwidth = %d\r\n", api.lora.pbw.get());

    delay(1000);
}
```
:::


#### set()

This API allow to set P2P Bandwidth in kHz (0 = 125, 1 = 250, 2 = 500, 3 = 7.8, 4 = 10.4, 5 = 15.63, 6 = 20.83, 7 = 31.25, 8 = 41.67, 9 = 62.5).

```c
api.lora.pbw.set(value);
```


| **Function**      | `bool set(uint32_t value)`                                                                    |
| ----------------- | --------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the P2P bandwidth                                                                 |
| **Returns**       | bool                                                                                          |
| **Return Values** | **TRUE** for setting P2P bandwidth success  <br>  **FALSE** for setting P2P bandwidth failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(1) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode bandwidth = %d\r\n", api.lora.pbw.get());

    delay(1000);
}
```
:::


### pcr

This API provides the configuration code rate for the P2P mode.


```c
RAKLora::pcr
```

#### get()

This API gets code rate for the P2P mode.

```c
api.lora.pcr.get();
```

| **Function** | `uint8_t get()` |
| ------------ | --------------- |
| **Returns**  | The code rate   |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode code rate = %d\r\n", api.lora.pcr.get());

    delay(1000);
}
```
:::


#### set()

This API sets code rate for the P2P mode.


```c
api.lora.pcr.set(value);
```

| **Function**      | `bool set(uint8_t value)`                                                            |
| ----------------- | ------------------------------------------------------------------------------------ |
| **Parameters**    | **value** - the code rate for P2P mode                                               |
| **Returns**       | bool                                                                                 |
| **Return Values** | **TRUE** for setting code rate success <br>  **FALSE** for setting code rate failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode code rate = %d\r\n", api.lora.pcr.get());

    delay(1000);
}
```
:::


### ppl


This API provides configuration Preamble Length for the P2P mode.


```c
RAKLora::ppl
```


#### get()

This API gets P2P Preamble Length (2-65535).


```c
api.lora.ppl.get();
```

| **Function** | `uint16_t get()`    |
| ------------ | ------------------- |
| **Returns**  | The Preamble length |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode preamble length = %d\r\n", api.lora.ppl.get());

    delay(1000);
}
```
:::

#### set()

This API sets P2P Preamble Length (2-65535).

```c
api.lora.ppl.set(value);
```

| **Function**   | `bool set(uint16_t value)`                                                                                        |
| -------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Parameters** | **value** - the P2P preamble length (2-65536)                                                                     |
| **Returns**    | **TRUE** for setting P2P preamble length success <br> **FALSE** for setting preamble length fail (Type: **bool**) |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode preamble length = %d\r\n", api.lora.ppl.get());

    delay(1000);
}

```
:::


### ptp

This API provides configuration power for the P2P mode.

```c
RAKLora::ptp
```

#### get()


This API gets P2P TX Power (5-22).


```c
api.lora.ptp.get();
```


| **Function** | `uint8_t value`           |
| ------------ | ------------------------- |
| **Returns**  | The Tx power for P2P mode |


::: details Click to View Example
```c{10}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode tx power = %d\r\n", api.lora.ptp.get());

    delay(1000);
}
```
:::

#### set()

This API sets P2P TX Power (5-22).


```c
api.lora.ptp.set(value);
```


| **Function**      | `bool set(uint8_t value)`                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the P2P Tx power                                                              |
| **Returns**       | bool                                                                                      |
| **Return Values** | **TRUE** for setting P2P Tx power success <br> **FALSE** for setting P2P Tx power failure |


::: details Click to View Example
```c{5}
void setup()
{
    Serial.begin(115200);
    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
}

void loop()
{
    Serial.printf("P2P mode tx power = %d\r\n", api.lora.ptp.get());

    delay(1000);
}

```
:::


### encry

This API configures P2P mode encryption.


```c
RAKLora::encry
```

#### get()

This API gets the status of P2P mode encryption.

```c
api.lora.encry.get();
```

| **Function**      | `bool get()`                                                                            |
| ----------------- | --------------------------------------------------------------------------------------- |
| **Returns**       | bool                                                                                    |
| **Return Values** | **TRUE**: P2P mode encryption is enable  <br> **FALSE**: P2P mode encryption is disable |


::: details Click to View Example
```c{21}
long startTime;
uint8_t node_encrypt_key[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t encrypt_buff[16];

void setup()
{
    Serial.begin(115200);
    startTime = millis();

    Serial.println("P2P Start");

    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption status %s\r\n", api.lora.encry.set(1) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption Key %s\r\n\r\n", api.lora.enckey.set(node_encrypt_key, 16) ? "Success" : "Fail");
    Serial.printf("P2P encryption status = %s\r\n", api.lora.encry.get() ? "Enable" : "Disable");

    api.lora.enckey.get(encrypt_buff, 16);
    Serial.printf("P2P encryption Key = 0x");
        for (int i = 0 ; i < 16 ; i++) {
            Serial.printf("%02X", encrypt_buff[i]);
        }
    Serial.println("");

    randomSeed(millis());
}

void loop()
{
    uint8_t payload[] = "payload";

    int rxDelay = random(3000, 5000);

    // Receive P2P data every 10 seconds
    if(millis() - startTime >= 10*1000) {
      Serial.printf("P2P Rx start for %d millisSeconds\r\n", rxDelay);
      startTime = millis();
      Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
      delay(rxDelay);
    } else {

      Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");
      delay(1000);
    }

}

```
:::

#### set()


This API enables or disables P2P mode encryption.


```c
api.lora.encry.set(value);
```

| **Function**      | `bool set(bool value)`                                                                                    |
| ----------------- | --------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **value** - the status of P2P mode encryption                                                             |
| **Returns**       | bool                                                                                                      |
| **Return Values** | **TRUE** for setting status of encryption success <br> **FALSE** for setting status of encryption failure |


::: details Click to View Example
```c{19}
long startTime;
uint8_t node_encrypt_key[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t encrypt_buff[16];

void setup()
{
    Serial.begin(115200);
    startTime = millis();

    Serial.println("P2P Start");

    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption status %s\r\n", api.lora.encry.set(1) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption Key %s\r\n\r\n", api.lora.enckey.set(node_encrypt_key, 16) ? "Success" : "Fail");

    Serial.printf("P2P encryption status = %s\r\n", api.lora.encry.get() ? "Enable" : "Disable");

    api.lora.enckey.get(encrypt_buff, 16);
    Serial.printf("P2P encryption Key = 0x");
        for (int i = 0 ; i < 16 ; i++) {
            Serial.printf("%02X", encrypt_buff[i]);
        }
    Serial.println("");

    randomSeed(millis());
}

void loop()
{
    uint8_t payload[] = "payload";

    int rxDelay = random(3000, 5000);

    // Receive P2P data every 10 seconds
    if(millis() - startTime >= 10*1000) {
      Serial.printf("P2P Rx start for %d millisSeconds\r\n", rxDelay);
      startTime = millis();
      Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
      delay(rxDelay);
    } else {

      Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");
      delay(1000);
    }
}

```
:::

### enckey

This API will encrypt the data being sent and received.

```c
RAKLora::enckey
```


#### get()

This API gets the key of P2P mode encryption.

```c
api.lora.enckey.get(buff, len);
```


| **Function**      | `bool get(uint8_t * buff, uint32_t len)`                                                                          |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **buff**	- the buffer to store encryption key <br> **len** - the length of encryption key (must be 16&nbsp;bytes) |
| **Returns**       | bool                                                                                                              |
| **Return Values** | **TRUE** for getting encryption key success <br> **FALSE** for getting encryption key failure                     |


::: details Click to View Example
```c{24}
long startTime;
uint8_t node_encrypt_key[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t encrypt_buff[16];

void setup()
{
    Serial.begin(115200);
    startTime = millis();

    Serial.println("P2P Start");

    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption status %s\r\n", api.lora.encry.set(1) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption Key %s\r\n\r\n", api.lora.enckey.set(node_encrypt_key, 16) ? "Success" : "Fail");

    Serial.printf("P2P encryption status = %s\r\n", api.lora.encry.get() ? "Enable" : "Disable");

    api.lora.enckey.get(encrypt_buff, 16);
    Serial.printf("P2P encryption Key = 0x");
        for (int i = 0 ; i < 16 ; i++) {
            Serial.printf("%02X", encrypt_buff[i]);
        }
    Serial.println("");

    randomSeed(millis());
}

void loop()
{
    uint8_t payload[] = "payload";

    int rxDelay = random(3000, 5000);

    // Receive P2P data every 10 seconds
    if(millis() - startTime >= 10*1000) {
      Serial.printf("P2P Rx start for %d millisSeconds\r\n", rxDelay);
      startTime = millis();
      Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
      delay(rxDelay);
    } else {

      Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");
      delay(1000);
    }

}

```
:::

#### set()


This API sets the key of P2P mode encryption.


```c
api.lora.enckey.set(buff, len);
```

| **Function**      | `bool set(uint8_t * buff, uint32_t len)`                                                                        |
| ----------------- | --------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **buff** - the buffer to set encryption key <br> **len** - the length of encryption key (must be 16&nbsp;bytes) |
| **Returns**       | bool                                                                                                            |
| **Return Values** | **TRUE** for setting encryption key success <br> **FALSE** for setting encryption failure                       |



::: details Click to View Example
```c{20}
long startTime;
uint8_t node_encrypt_key[16] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
uint8_t encrypt_buff[16];

void setup()
{
    Serial.begin(115200);
    startTime = millis();

    Serial.println("P2P Start");

    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption status %s\r\n", api.lorawan.encry.set(1) ? "Success" : "Fail");
    Serial.printf("Set P2P mode encryption Key %s\r\n\r\n", api.lorawan.enckey.set(node_encrypt_key, 16) ? "Success" : "Fail");

    Serial.printf("P2P encryption status = %s\r\n", api.lorawan.encry.get() ? "Enable" : "Disable");

    api.lorawan.enckey.get(encrypt_buff, 16);
    Serial.printf("P2P encryption Key = 0x");
        for (int i = 0 ; i < 16 ; i++) {
            Serial.printf("%02X", encrypt_buff[i]);
        }
    Serial.println("");

    randomSeed(millis());
}

void loop()
{
    uint8_t payload[] = "payload";

    int rxDelay = random(3000, 5000);

    // Receive P2P data every 10 seconds
    if(millis() - startTime >= 10*1000) {
      Serial.printf("P2P Rx start for %d millisSeconds\r\n", rxDelay);
      startTime = millis();
      Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
      delay(rxDelay);
    } else {

      Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");
      delay(1000);
    }

}

```
:::


### pbr


This API configures the P2P FSK modem bitrate (600&nbsp;b/s - 307200&nbsp;b/s).

```c
RAKLora::pbr
```

#### get()

This API gets the P2P FSK modem bitrate (600&nbsp;b/s - 307200&nbsp;b/s).

```c
api.lora.pbr.get();
```

| **Function** | `uint32_t get()`          |
| ------------ | ------------------------- |
| **Returns**  | The P2P FSK modem bitrate |


#### set()

This API sets the P2P FSK modem bitrate (600&nbsp;b/s - 307200&nbsp;b/s).


```c
api.lora.pbr.get();
```


| **Function**   | `bool set(uint32_t value)` |
| -------------- | -------------------------- |
| **Parameters** | value                      |


### pfdev

This API configures the P2P FSK modem frequency deviation.

```c
RAKLora::pfdev
```

#### get()

This API gets the P2P FSK modem frequency deviation.

```c
api.lora.pfdev.get();
```

| **Function** | `uint32_t get()`                      |
| ------------ | ------------------------------------- |
| **Returns**  | The P2P FSK modem frequency deviation |



#### set()


This API sets the P2P FSK modem frequency deviation.

```c
api.lora.pfdev.set(value);
```

| **Function**   | `bool set(uint32_t value)` |
| -------------- | -------------------------- |
| **Parameters** | value                      |


### registerPRecvCallback()

This API registers a callback function, so that application can be notified on receiving P2P data.

```c
api.lora.registerPRecvCallback(service_lora_p2p_recv_cb_type callback);
```


| **Function**      | `bool registerPRecvCallback(service_lora_p2p_recv_cb_type callback)`                                |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** - callback function                                                                         |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |


::: details Click to View Example
```c{28}
void recv_cb(rui_lora_p2p_recv_t data) {
  Serial.println("Receive something");
}

void send_cb(void) {
  Serial.println("I send something");
}

long startTime;

void setup()
{
  Serial.begin(115200);

  delay(2000);
  startTime = millis();

  Serial.println("P2P Start");

  Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
  Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
  Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
  Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
  Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
  Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
  Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");

  api.lora.registerPRecvCallback(recv_cb);
  api.lora.registerPSendCallback(send_cb);

  randomSeed(millis());
}

void loop()
{
  uint8_t payload[] = "payload";

  int rxDelay = random(3000, 5000);

  // Receive P2P data every 10 seconds
  if(millis() - startTime >= 10*1000) {
    Serial.printf("P2P Rx start for %d millisSeconds\r\n", rxDelay);
    startTime = millis();
    Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
    delay(rxDelay);
  } else {

    Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");
    delay(1000);
  }
}

```
:::

### registerPSendCallback()

This API registers a callback function, so that application can be notified when P2P uplink process is done.

```c
api.lora.registerPSendCallback(service_lora_p2p_send_cb_type callback);
```

| **Function**      | `bool registerPSendCallback(service_lora_p2p_send_cb_type callback)`                                |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** - callback function                                                                         |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |



::: details Click to View Example
```c{29}
void recv_cb(rui_lora_p2p_recv_t data) {
  Serial.println("Receive something");
}

void send_cb(void) {
  Serial.println("I send something");
}

long startTime;

void setup()
{
  Serial.begin(115200);

  delay(2000);
  startTime = millis();

  Serial.println("P2P Start");

  Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
  Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
  Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
  Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
  Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
  Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
  Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");

  api.lora.registerPRecvCallback(recv_cb);
  api.lora.registerPSendCallback(send_cb);

  randomSeed(millis());
}

void loop()
{
  uint8_t payload[] = "payload";

  int rxDelay = random(3000, 5000);

  // Receive P2P data every 10 seconds
  if(millis() - startTime >= 10*1000) {
    Serial.printf("P2P Rx start for %d millisSeconds\r\n", rxDelay);
    startTime = millis();
    Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
    delay(rxDelay);
  } else {

    Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");
    delay(1000);
  }

}

```
:::

### registerPSendCADCallback()

This API registers a callback function, so that application can be notified about the result of CAD (Channel Activity Detection).

```c
api.lora.registerPSendCADCallback(service_lora_p2p_send_CAD_cb_type callback);
```

| **Function**      | `bool registerPSendCallback(service_lora_p2p_send_CAD_cb_type callback)`                                |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Parameters**    | **The** - callback function                                                                         |
| **Returns**       | bool                                                                                                |
| **Return Values** | **TRUE** for setting callback function success <br> **FALSE** for setting callback function failure |



::: details Click to View Example
```c{29}
void recv_cb(rui_lora_p2p_recv_t data) {
	Serial.println("Receive something");
}

void send_cb(void) {
	Serial.println("I send something");
}

void cad_cb(bool detect) {
	if(detect)
		Serial.println("detect Activity");
	else
		Serial.println("no Activity");
}


long startTime;

void setup()
{
	Serial.begin(115200);

	delay(2000);
	startTime = millis();

	Serial.println("P2P Start");

	Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
	Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
	Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
	Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
	Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
	Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
	Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");

	api.lora.registerPRecvCallback(recv_cb);
	api.lora.registerPSendCallback(send_cb);
	api.lora.registerPSendCADCallback(cad_cb);

	randomSeed(millis());
}

void loop()
{
	uint8_t payload[] = "payload";

	int rxDelay = random(3000, 5000);

	// Receive P2P data every 10 seconds
	if(millis() - startTime >= 10*1000) {
		Serial.printf("P2P Rx start for %d millisSconds\r\n", rxDelay);
		startTime = millis();
		Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(rxDelay) ? "Success" : "Fail");
		delay(rxDelay);
	} else {
		// Send packet with CAD enabled
		Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload, TRUE)? "Success" : "Fail");
		delay(1000);
	}
}
```
:::

### psend()

This API provides the way to P2P send data.

:::tip 📝 NOTE
- P2P TX mode can be blocked by certain settings in P2P RX mode. To ensure that P2P RX mode is not blocking the `psend()` API, you can disable P2P RX mode and switch to P2P TX mode via `api.lora.precv(0)`.
- By default, CAD is disabled. When CAD mode is enabled, the device will continue to check for channel activity until it can send the packet.
:::


```c
api.lora.psend(length, payload, ena_cad);
```

| **Function**      | `bool psend(uint8_t length, uint8_t * payload, bool ena_cad)`                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Parameters**    | **length** - the length of the payload <br> **payload** - the data send to the other device <br> **ena_cad** - enable (TRUE) or disable (FALSE) CAD before sending |
| **Returns**       | bool                                                                                                                                                               |
| **Return Values** | **TRUE**  for sending data success <br> **FALSE** for sending data failure                                                                                         |


::: details Click to View Example
```c{19}
void setup()
{
    Serial.begin(115200);

    Serial.println("P2P Start");

    Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
    Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
    Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
    Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
    Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
    Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
    Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
}

void loop()
{
    uint8_t payload[] = "payload";
	// Send packet with CAD disabled
    Serial.printf("P2P send %s\r\n", api.lora.psend(sizeof(payload), payload)? "Success" : "Fail");

    delay(5000);
}

```
:::


### precv()

This API is used to enter P2P RX mode for a specified period.

```c
api.lora.precv(uint32_t timeout)
```

| **Function**      | `bool precv(uint32_t timeout)`                                                                                                                                                                                                                                                                                                                 |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Parameters**    | **timeout** - the duration of P2P Rx mode in milliseconds <br> Special timeout values: <br> **65535**: Stay in RX mode until a packet is received. <br> **65534**: Permanent RX mode (TX not possible) until `api.lora.precv(0)` is executed. <br> **65533**: Permanent RX mode and still allows TX without calling `api.lora.precv(0)`. |
| **Returns**       | bool                                                                                                                                                                                                                                                                                                                                           |
| **Return Values** | **TRUE** for entering P2P Rx mode success <br> **FALSE** for failure to activate P2P RX mode                                                                                                                                                                                                                                                   |


::: details Click to View Example
```c{18}
void setup()
  {
      Serial.begin(115200);

      Serial.println("P2P Start");

      Serial.printf("Set Node device work mode %s\r\n", api.lora.nwm.set() ? "Success" : "Fail");
      Serial.printf("Set P2P mode frequency %s\r\n", api.lora.pfreq.set(868000000) ? "Success" : "Fail");
      Serial.printf("Set P2P mode spreading factor %s\r\n", api.lora.psf.set(12) ? "Success" : "Fail");
      Serial.printf("Set P2P mode bandwidth %s\r\n", api.lora.pbw.set(125) ? "Success" : "Fail");
      Serial.printf("Set P2P mode code rate %s\r\n", api.lora.pcr.set(0) ? "Success" : "Fail");
      Serial.printf("Set P2P mode preamble length %s\r\n", api.lora.ppl.set(8) ? "Success" : "Fail");
      Serial.printf("Set P2P mode tx power %s\r\n", api.lora.ptp.set(22) ? "Success" : "Fail");
  }

  void loop()
  {
      Serial.printf("P2P set Rx mode %s\r\n",api.lora.precv(5000) ? "Success" : "Fail");

      delay(6000);
  }

```
:::


