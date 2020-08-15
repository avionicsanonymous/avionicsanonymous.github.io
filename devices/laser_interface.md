# Laser Altimeter Interface

## Overview

The [Avionics Anonymous Laser Altimeter Interface](https://www.tindie.com/products/avionicsanonymous/uavcan-laser-altimeter-interface/) is a tiny interface for [several common laser rangefinders](#supported_rangefinders) that allows connection to Pixhawk and other similar autopilots via UAVCAN - A nice robust interface, no sketchy long-distance I2C wiring and no hogged serial ports! These lasers are great for use as laser altimeters which help with nice auto landings. Comes fully assembled, ready to use!

### Currently supported lasers {#supported_rangefinders}:

At time of writing the following rangefinders are supported:

- Lightware SF30/D
- Lightware SF10/a
- Lightware SF10/b
- Lightware SF10/c
- Lightware SF11/b
- Lightware SF11/c

Coming soon:

- Lidar Lite
- Others - contact us with your needs!

## What makes it special?

- Robust UAVCAN interface is compatible with most Pixhawks and similar autopilots and makes it safe to install your laser far away from the autopilot, wherever is convenient!
- Onboard power filtering for connected laser
- Mount with screws through mounting ears or snip them off and foam tape it straight to your laser
- Update firmware via CAN interface

## Specifications

    Weight: 3.2 grams
    Size: 1.25in x 0.75in x 0.25in
    Power: 4.0V to 5.5V, XXmA

## Required Accessories

    JST-GH Interconnect Cable for connection to Pixhawk 2.1, Pixhawk 4, etc
    JST-GH CAN Terminator (connects to the last device on the CAN bus)

## Where to Buy

* [AvAnon Laser Interface](https://www.tindie.com/products/avionicsanonymous/uavcan-laser-altimeter-interface/)

## Wiring

The rangefinder (laser) is connected to the AvAnon interface board, which is connected to one of the CAN ports on your autopilot.
The wiring is as per the pinout below, or the necessary cables can be purchased to connect to your system right out of the box. 
These are available at the links [here](https://www.tindie.com/products/avionicsanonymous/uavcan-laser-altimeter-interface/).

The interface board provides a filtered power output for the laser, but does not provide its own regulation.
Therefore, the laser must be compatible with whatever voltage is supplied to the board.

### Pinouts

#### CAN Connector
Pin | Name | Description
--- | ---   | ---
1   | POWER_IN | Power Supply. 4.0-5.5V supported, but must also be compatible with connected laser.
2   | TX/SCL | TX for serial mode, Clock for I2C mode
3   | RX/SDA | RX for serial mode, Data for I2C mode
4   | GND | Signal/power ground.

#### Laser Connector

Pin | Name | Description
--- | ---   | ---
1   | POWER_OUT | Filtered power at the supply voltage.
2   | CAN+ | TX for serial mode, Clock for I2C mode
3   | RX/SDA | RX for serial mode, Data for I2C mode
4   | GND | Signal/power ground.


## Configuration

### Autopilot Configuration - PX4
Several parameters must be set using QGC or similar:
- UAVCAN must be enabled by setting UAVCAN_ENABLE non zero. Set this to 1 for basic functionality or 2 to allow the device's UAVCAN parameters to be accessed via QGC.
- The minimum and maximum valid range for the laser must be set in the parameters UAVCAN_RNG_MIN and UAVCAN_RNG_MAX. These should be set according to the manufacturer's datasheet.

### Device Configuration
The Laser Interface has a number of parameters accessible via the UAVCAN interface. These may be accessed by either:
- Configuring the PX4 "UAVCAN_ENABLE" parameter to "2" and using QGC to access the parameters via the same page where autopilot parameters are adjusted. The CAN devices' parameters will appear at the bottom of the parameter list.
- Using an SLCAN tool, such as the [Zubax Babel](https://zubax.com/products/babel) and the [UAVCAN GUI](https://github.com/UAVCAN/gui_tool)

#### Parameters
Parameter Name      | Description                                           | Valuess
---                 | ---                                                   | ---
node_id             | Node ID for this device                               | 1-125
rangefinder_hw      | Rangefinder type specifier - see list below           | 1-10 (see below)
first_return        | Use "first" or "last" return range, if supported by rangefinder   | 0 = last return, 1 = first return

#### Rangefinder Hardware Options
Rangefinder Model   | rangefinder_hw Value     | Wiring Type
---                 | ---                   | ---
Lightware SF02      | 1                     | Serial
Lightware SF10/a    | 2                     | Serial
Lightware SF10/b    | 3                     | Serial
Lightware SF10/c    | 4                     | Serial
Lightware SF11/c    | 5                     | Serial
Lightware SF11/b    | 6                     | Serial
Lightware SF30/D    | 10                    | Serial


