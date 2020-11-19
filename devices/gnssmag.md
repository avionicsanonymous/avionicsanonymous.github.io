# GNSSMag

## Overview

![GNSSMag GPS and Magnetometer](../.gitbook/assets/gnssmag.png)

The [Avionics Anonymous GNSSMag GPS and Magnetometer](https://www.avionicsanonymous.com/product-page/uavcan-gnss-mag) is a combination GPS and magnetometer for small unmanned aircraft. Includes a uBlox SAM-M8Q integrated multi-constellation GNSS unit and a high-quality Memsic MMC5983MA magnetometer enabling sub-1-degree heading accuracy. All of this interfaces to your autopilot via robust UAVCAN interface - no sketchy I2C wiring for your magnetometer! Comes fully assembled, ready to plug in and use! Also available without a magnetometer for applications using remote mags.

### What makes it special?

* Extremely high-quality Memsic magnetometer IC allows ~0.5deg heading accuracy in low-interference installations
* uBlox multi-constellation GPS provides excellent performance in any flying scenario
* Robust UAVCAN interface is compatible with most Pixhawks and similar autopilots and makes it safe to install your laser far away from the autopilot, wherever is convenient!
* Broken-out GPS interrupt pin for special timing applications
* Drop-in replacement for competitive UAVCAN GPS/magnetometer unit
* Update firmware via CAN interface

### Specifications

* Weight: 16.9 grams
* Size: 55m x 55mm x 10mm
* Power: 4.0V to 5.5V, XXmA

### Required Accessories

* [CAN Harness](https://www.avionicsanonymous.com/product-page/uavcan-interconnect-cable) - connects between the autopilot and a CAN node and between each CAN node on the bus
* [CAN Terminator](https://www.avionicsanonymous.com/product-page/uavcan-terminator) - connects to the last device on the CAN bus

#### Where to Buy

* [Avionics Anonymous Store](https://www.avionicsanonymous.com/product-page/uavcan-gnss-mag)
* [Tindie](https://www.tindie.com/products/avionicsanonymous/uavcan-gps-magnetometer/)

## User Guide

### Wiring

The GNSSMag is connected to your autopilot via CAN bus. The wiring is per the pinout below, or the necessary cables can be purchased to connect to your system right out of the box:

* [CAN Harness](https://www.avionicsanonymous.com/product-page/uavcan-interconnect-cable) - connects between the autopilot and a CAN node and between each CAN node on the bus
* [CAN Terminator](https://www.avionicsanonymous.com/product-page/uavcan-terminator) - connects to the last device on the CAN bus

#### Pinouts

**CAN Connector**

| Pin | Name | Description |
| :--- | :--- | :--- |
| 1 | POWER\_IN | Power Supply. 4.0-5.5V supported. |
| 2 | CAN\_H | CAN high |
| 3 | CAN\_L | CAN low |
| 4 | GND | Signal/power ground. |

**AUX Connector**

| Pin | Name | Description |
| :--- | :--- | :--- |
| 1 | EXTINT | GPS external interrupt input. Normally unused. |
| 2 | Reserved | Reserved for future use |
| 3 | PPS | GPS Pulse-Per-Second output |

### Configuration

#### Autopilot Configuration

**PX4**

Several autopilot parameters must be set using QGC or similar:

* UAVCAN must be enabled by setting _UAVCAN\_ENABLE_ non zero. Set this to 1 for basic functionality or 2 to allow the device's UAVCAN parameters to be accessed via QGC.

#### Node Configuration

The GNSSMag node has a number of parameters accessible via the UAVCAN interface. These may be set following the steps outlined [here](../general/parameters.md)

**Parameters**

| Parameter Name | Description | Default Value | Allowable Values |
| :--- | :--- | :--- | :--- |
| node\_id | Node ID for this device | 120 | 1-125 |
| rotation | Board rotation in degrees | 0 | 0-360 |
| update\_rate\_hz | Rate at which magnetic field data is published in Hz | 30 | 0-30 |
| auto\_mag\_set | Enable [auto temperature compensation](gnssmag.md#automatic-temperature-compensation) | 0 | 0-1 |

**Automatic Temperature Compensation**

Setting the "auto\_mag\_set" parameter to 1 enables an experimental automatic temperature compensation. When enabled, every 10 seconds, the unit evaluates its internal temperature. if it has changed too much, the unit performs an automatic reset and set of the polarity of the sensing film and uses this to update thermal correction offsets. If the sensor undergoes significant changes in ambient temperature, this can dramatically improve stability and accuracy of its output, but also leads to small step changes in the magnetic field output when the offsets are updated. This will pose no issue for PX4 autopilots which fuse magnetic data into a Kalman filter, but you should ensure this behavior is safe in your application. Please contact us for more information.

**Warning** This feature has not been thoroughly vetted and is considered experimental! Use at your own risk.

