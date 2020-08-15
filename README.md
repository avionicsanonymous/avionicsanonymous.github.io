<div style="float:right; padding:10px; margin-right:20px;"><a href="http://avionicsanonymous.github.com"></a></div>

# Avionics Anonymous Device User Guide

PX4 is the *Professional Autopilot*. 
Developed by world-class developers from industry and academia, and supported by an active world wide community, it powers all kinds of vehicles from racing and cargo drones through to ground vehicles and submersibles.

> **Tip** This guide contains everything you need to connect, configure, and use your Avionics Anonymous peripherals.

<span></span>
> **Note** This guide is still a work in progress! Please contact us if you have questions not addressed here.

## How Do I Get Started?

[Getting Started](getting_started/README.md) should be read by all users! 
It provides an overview of PX4, including features provided by the flight stack (flight modes and safety features) and the supported hardware (flight controller, vehicles, airframes, telemetry systems, RC control systems).

Depending on what you want to achieve, the following tips will help you navigate through this guide:

**I already have a drone and I just want to fly:**

If you have a Ready To Fly (RTF) vehicle that supports PX4:

- [Basic Configuration](config/README.md) explains how to update your firmware to the latest version, calibrate the main sensors (compass, gyro/IMU, airspeed etc.), and setup your remote control and safety features.
- [Flying](flying/README.md) teaches flight essentials, including where and how to fly safely, and how to debug arming and flight issues. It also provides detailed information about flight modes.


**I want to build a drone with PX4 from scratch:**

> **Tip** The "supported" vehicles are listed in the [Airframes Reference](airframes/airframe_reference.md). 
  These are vehicles that have tested and tuned configurations that you can download using *QGroundControl*. 

If you want to build a vehicle from scratch:

- Choose a frame - [Airframe Builds](airframes/README.md) lists the supported frames and provides detailed instructions for how to construct a subset of vehicles.
- Choose a flight controller - see [Getting Started > Flight Controllers](getting_started/flight_controller_selection.md) and [Autopilot Hardware](flight_controller/README.md).
- [Assembly](assembly/README.md) explains how to wire up the important peripherals to your autopilot.
- [Basic Configuration](config/README.md) shows how to update your firmware and configure it with settings appropriate for your airframe. 
  This section also explains how to calibrate the main sensors (compass, gyro/IMU, airspeed etc.), and setup your remote control and safety features.

Once you are ready to fly your vehicle, visit the [Flying](flying/README.md) section.


**I am modifying a supported vehicle:**

Modifications of the flight controller and basic sensors are covered above. 
In order to use new sensors, or if you have made changes that significantly affect flight characteristics: 

- [Peripheral Hardware](peripherals/README.md) provides additional information about using external sensors.
- [Basic Configuration](config/README.md) explains how to calibrate the main sensors.
- [Advanced Configuration](advanced_config/README.md) should be used to re/fine-tune the airframe.


**I want to run PX4 on new hardware and extend the platform:**

- [PX4 Developer Guide](http://dev.px4.io/) explains how to modify flight algorithms, add new modes, integrate new hardware, communicate with PX4 from outside the flight controller, and contribute to PX4.
