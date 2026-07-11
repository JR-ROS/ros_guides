# Guides for the Just Robotics Bot

This is the documentation for the Just Robotics Bot (JR Bot). The actual robot code resides in separate repositories.

| Repository | Description |
| --- | --- |
| [JR-ROS/jr_bot_firmware](https://github.com/JR-ROS/jr_bot_firmware) | The C++ firmware for the ESP32 microcontroller on the JR Bot, written using the Arduino framework in PlatformIO. |
| [JR-ROS/jr_bot_ros](https://github.com/JR-ROS/jr_bot_ros) | The ROS2 code for the JR Bot, written in Python and C++. This code runs on a computer and communicates with the ESP32 firmware over USB. |
| [JR-ROS/docker-containers](https://github.com/JR-ROS/docker-containers) | Docker containers for the JR Bot, including a host container that runs the ROS2 code and communicates with the ESP32 firmware. |


## Guides included in this repository

It would be a good idea to use the guides in the order they are presented here, as they build on each other.

| Order | Guide | Description |
| --- | --- | --- |
| 1 | [Post Ubuntu Setup](src/setup_ubuntu.md) | Instructions for setting up Ubuntu, including installing ROS2 and Docker. |
| 2 | [USB Guide](src/usb.md) | Instructions for setting up USB access to the ESP32 on Ubuntu. |
| 3 | [JR Bot Setup](src/jr_bot_setup.md) | Instructions for downloading the JR Bot code, uploading the firmware to the ESP32, and running the ROS2 code in a Docker container. |