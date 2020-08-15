# Laser Interface

The [Avionics Anonymous Laser Altimeter Interface](https://www.tindie.com/products/avionicsanonymous/uavcan-laser-altimeter-interface/) is a tiny interface for [several common laser rangefinders](laser_interface.md#currently-supported-lasers) that allows connection to Pixhawk and other similar autopilots via UAVCAN - A nice robust interface, no sketchy long-distance I2C wiring and no hogged serial ports! These lasers are great for use as laser altimeters which help with nice auto landings. Comes fully assembled, ready to use!

## Currently supported Lasers

At time of writing the following rangefinders are supported:

* Lightware SF02
* Lightware SF10/a
* Lightware SF10/b
* Lightware SF10/c
* Lightware SF11/b
* Lightware SF11/c
* Lightware SF\(LW\)20/b
* Lightware SF\(LW\)20/c
* Lightware SF30/D

Coming soon:

* Lidar Lite
* Others - contact us with your needs!

## What makes it special?

* Robust UAVCAN interface is compatible with most Pixhawks and similar autopilots and makes it safe to install your laser far away from the autopilot, wherever is convenient!
* Onboard power filtering for connected laser
* Mount with screws through mounting ears or snip them off and foam tape it straight to your laser
* Update firmware via CAN interface

## Specifications

* Weight: 3.2 grams  
* Size: 1.25in x 0.75in x 0.25in  
* Power: 4.0V to 5.5V, XXmA  

## Required Accessories

* [CAN Harness](https://www.tindie.com/products/avionicsanonymous/uavcan-interconnect-cable/) - connects between the autopilot and a CAN node and between each CAN node on the bus
* [CAN Terminator](https://www.tindie.com/products/avionicsanonymous/uavcan-jst-terminator/) - connects to the last device on the CAN bus

## Where to Buy

* [Tindie](https://www.tindie.com/products/avionicsanonymous/uavcan-laser-altimeter-interface/)

# User Guide

## Wiring

The rangefinder \(laser\) is connected to the AvAnon Laser Interface board, which is connected to one of the CAN ports on your autopilot. The wiring is per the pinout below, or the necessary cables can be purchased to connect to your system right out of the box:

* [CAN Harness](https://www.tindie.com/products/avionicsanonymous/uavcan-interconnect-cable/) - connects between the autopilot and a CAN node and between each CAN node on the bus
* [CAN Terminator](https://www.tindie.com/products/avionicsanonymous/uavcan-jst-terminator/) - connects to the last device on the CAN bus

The interface board provides a filtered power output for the laser, but does not provide its own regulation. Therefore, the laser must be compatible with whatever voltage is supplied to the Laser Interface.

### Pinouts

**CAN Connector**

| Pin | Name | Description |
| :--- | :--- | :--- |
| 1 | POWER\_IN | Power Supply. 4.0-5.5V supported, but must also be compatible with connected laser. |
| 2 | TX/SCL | TX for serial mode, Clock for I2C mode |
| 3 | RX/SDA | RX for serial mode, Data for I2C mode |
| 4 | GND | Signal/power ground. |

**Laser Connector**

| Pin | Name | Description |
| :--- | :--- | :--- |
| 1 | POWER\_OUT | Filtered power at the supply voltage. |
| 2 | CAN\_H | CAN high |
| 3 | CAN\_L | CAN low |
| 4 | GND | Signal/power ground. |

## Configuration

### Autopilot Configuration

**PX4**

Several autopilot parameters must be set using QGC or similar:

* _UAVCAN_ must be enabled by setting UAVCAN\_ENABLE non zero. Set this to 1 for basic functionality or 2 to allow the device's UAVCAN parameters to be accessed via QGC.
* The minimum and maximum valid range for the laser must be set in the parameters _UAVCAN\_RNG\_MIN_ and _UAVCAN\_RNG\_MAX_. These should be set according to the rangefinder manufacturer's datasheet.

### Rangefinder Configuration

Certain parameters must be configured in your rangefinder per the manufacturer's guidance

| Rangefinder Model | Notes |
| :--- | :--- |
| Lightware SF02 | Must be set to 115200 baud |
| Lightware SF10/a | Must be set to 115200 baud |
| Lightware SF10/b | Must be set to 115200 baud |
| Lightware SF10/c | Must be set to 115200 baud |
| Lightware SF11/c | Must be set to 115200 baud |
| Lightware SF11/b | Must be set to 115200 baud |
| Lightware SF\(LW\)20/b | Must be set to 115200 baud. Returns default distance. |
| Lightware SF11/b | Must be set to 115200 baud. Returns default distance. |
| Lightware SF30/D | Must be set to 115200 baud. Returns default distance. |

### Node Configuration

The Laser Interface node has a number of parameters accessible via the UAVCAN interface. These may be set following the steps outlined [here](../general/parameters.md)

**Parameters**

| Parameter Name | Description | Values |
| :--- | :--- | :--- |
| node\_id | Node ID for this device | 1-125 |
| rangefinder\_hw | Rangefinder type specifier - see list below | 1-10 \(see below\) |
| first\_return | Use "first" or "last" return range, if supported by rangefinder | 0 = last return, 1 = first return |

**Rangefinder Hardware Options**

| Rangefinder Model | rangefinder\_hw Value | Wiring Type |
| :--- | :--- | :--- |
| Lightware SF02 | 1 | Serial |
| Lightware SF10/a | 2 | Serial |
| Lightware SF10/b | 3 | Serial |
| Lightware SF10/c | 4 | Serial |
| Lightware SF11/c | 5 | Serial |
| Lightware SF11/b | 6 | Serial |
| Lightware SF\(LW\)20/b | 7 | Serial |
| Lightware SF11/b | 8 | Serial |
| Lightware SF30/D | 10 | Serial |

