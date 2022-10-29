| <center><img src="./assets/rakstar.jpg" alt="RAKstar" width=25%></center>  | ![RAKWireless](./assets/RAK-Whirls.png) | [![Build Status](https://github.com/RAKWireless/RAK13800-W5100S/workflows/RAK%20Library%20Build%20CI/badge.svg)](https://github.com/RAKWireless/RAK13800-W5100S/actions) |
| -- | -- | -- |

# RAK13800_W5100S_Ethernet_library

Rakwireless W5100S Ethernet library is modified from Arduino Ethernet library (V2.0.0) for the Arduino platform, because this library is very comprehensive and supports W5100/W5200/W5500 devices. We have added support for W5100S and made adaptations to RAK4631, RAK11200, and RAK11300 platforms.

[*RAKWireless <RAK#> <function>*](https://store.RAKWireless.com/products/rak13800)

# Documentation

* **[Product Repository](https://github.com/RAKWireless/RAK13800_W5100S)** - Product repository for the RAKWireless RAK13005 LIN Bus module.
* **[Documentation](https://docs.RAKWireless.com/Product-Categories/WisBlock/RAK13800/Overview/)** - Documentation and Quick Start Guide for the RAK13800 Ethernet module.

# Installation

In Arduino IDE open Sketch->Include Library->Manage Libraries then search for RAK13800.

In PlatformIO open PlatformIO Home, switch to libraries and search for RAK13005.
Or install the library project dependencies by adding

```log
lib_deps =
  RAKWireless/RAK13800_W5100S
```

into **`platformio.ini`**

For manual installation download the archive, unzip it and place the RAK13800_W5100S folder into the library directory.
In Arduino IDE this is usually <arduinosketchfolder>/libraries/
In PlatformIO this is usually <user/.platformio/lib>

# Usage

The library provides an interface class, which allows communication with W5100S via SPI. These examples show how to use RAK13800.

- [RAK13800_Ethernet_DHCP_W5100S](./examples/RAK13800_Ethernet_DHCP_W5100S) Get an IP address via DHCP and print the address obtained.
- [RAK13800_Ethernet_HTTP_Client_W5100S](./examples/RAK13800_Ethernet_HTTP_Client_W5100S) This example connects to a website (http://www.google.com).
- [RAK13800_Ethernet_HTTP_Server_W5100S](./examples/RAK13800_Ethernet_HTTP_Server_W5100S) A simple web server that shows the value of the analog input pins.
- [RAK13800_Ethernet_MQTT_Publish_W5100S](./examples/RAK13800_Ethernet_MQTT_Publish_W5100S) This example connects to a MQTT broker and publishes a message to a topic once a second.
- [RAK13800_Ethernet_MQTT_Subscribes_W5100S](./examples/RAK13800_Ethernet_MQTT_Subscribes_W5100S) This example connects to a MQTT broker and subscribes to a single topic. When a message is received it prints the message to the serial monitor.
- [RAK13800_Ethernet_TCP_Client_W5100S](./examples/RAK13800_Ethernet_TCP_Client_W5100S) Establish connection with TCP server and send data.
- [RAK13800_Ethernet_TCP_Server_W5100S](./examples/RAK13800_Ethernet_TCP_Server_W5100S) A simple server can communicate with any connected TCP client.
- [RAK13800_Ethernet_UDP_W5100S](./examples/RAK13800_Ethernet_UDP_W5100S) Receives UDP message strings, prints them to the serial port and sends an "acknowledge" string back to the sender.

## This class provides the following methods:

**Notes: Below is the important API. For more, please look the [official instructions](https://www.arduino.cc/en/Reference/Ethernet).**

**static void begin(uint8_t *mac, IPAddress ip);
static void begin(uint8_t *mac, IPAddress ip, IPAddress dns);
static void begin(uint8_t *mac, IPAddress ip, IPAddress dns, IPAddress gateway);
static void begin(uint8_t *mac, IPAddress ip, IPAddress dns, IPAddress gateway, IPAddress subnet);**

Initializes the ethernet library and network settings.

#### Parameters:

| Direction | Name    | Function                                                     |
| --------- | ------- | ------------------------------------------------------------ |
| in        | mac     | The MAC (Media access control) address for the device (array of 6 bytes). this is the Ethernet hardware address of your shield. Newer Arduino Ethernet Shields include a sticker with the device's MAC address. For older shields, choose your own. |
| in        | ip      | The IP address of the device (array of 4 bytes).             |
| in        | dns     | The IP address of the DNS server (array of 4 bytes). optional: defaults to the device IP address with the last octet set to 1. |
| in        | gateway | The IP address of the network gateway (array of 4 bytes). optional: defaults to the device IP address with the last octet set to 1. |
| in        | subnet  | The subnet mask of the network (array of 4 bytes). optional: defaults to 255.255.255.0. |
| return    |         | The DHCP version of this function, Ethernet.begin(mac), returns an int: 1 on a successful DHCP connection, 0 on failure. The other versions don't return anything. |

**static void init(uint8_t sspin = 10);**

Used to configure the CS (chip select) pin for the Ethernet controller chip. The Ethernet library has a default CS pin, which is usually correct, but with some non-standard Ethernet hardware you might need to use a different CS pin.

#### Parameters:

| Direction | Name  | Function                             |
| --------- | ----- | ------------------------------------ |
| in        | sspin | The pin number to use for CS (byte). |
| return    |       | none                                 |

**static IPAddress localIP();**

Obtains the IP address of the Ethernet shield. Useful when the address is auto assigned through DHCP.

#### Parameters:

| Direction | Name     | Function        |
| --------- | -------- | --------------- |
| in        | local_ip | none            |
| return    |          | The IP address. |

**static void MACAddress(uint8_t *mac_address);**

Fills the supplied buffer with the MAC address of the device.

#### Parameters:

| Direction | Name        | Function                                              |
| --------- | ----------- | ----------------------------------------------------- |
| in        | mac_address | Buffer to receive the MAC address (array of 6 bytes). |
| return    |             | none                                                  |

**static IPAddress gatewayIP();**

Returns the gateway IP address for the device.

#### Parameters:

| Direction | Name | Function                                           |
| --------- | ---- | -------------------------------------------------- |
| in        |      | none                                               |
| return    |      | The gateway IP address for the device (IPAddress). |

**void setLocalIP(const IPAddress local_ip);**

Set the IP address of the device. Not for use with DHCP.

#### Parameters:

| Direction | Name     | Function                          |
| --------- | -------- | --------------------------------- |
| in        | local_ip | The IP address to use (IPAddress) |
| return    |          | none                              |

**void setMACAddress(const uint8_t *mac_address);**

Set the MAC address. Not for use with DHCP.

#### Parameters:

| Direction | Name        | Function                                   |
| --------- | ----------- | ------------------------------------------ |
| in        | mac_address | The MAC address to use (array of 6 bytes). |
| return    |             | none                                       |

**void setGatewayIP(const IPAddress gateway);**

Set the IP address of the network gateway. Not for use with DHCP.

#### Parameters:

| Direction | Name    | Function                                          |
| --------- | ------- | ------------------------------------------------- |
| in        | gateway | The IP address of the network gateway (IPAddress) |
| return    |         | none                                              |

**static EthernetHardwareStatus hardwareStatus();**

`Ethernet.hardwareStatus()` tells you which WIZnet Ethernet controller chip was detected during `Ethernet.begin()`, if any. This can be used for troubleshooting. If no Ethernet controller was detected then there is likely a hardware problem.

#### Parameters:

| Direction | Name | Function                                                     |
| --------- | ---- | ------------------------------------------------------------ |
| in        |      | none                                                         |
| return    |      | which WIZnet Ethernet controller chip was detected during `Ethernet.begin()` (EthernetHardwareStatus) |

