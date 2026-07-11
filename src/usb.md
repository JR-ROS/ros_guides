# Introduction

In general, devices like ESP32, Arduino, LiDARs etc connect to a specific port on your laptop. On Windows, these are called COM ports and have a number (like COM3, COM7, COM4 etc, generalised as COMx). On Linux, these are called tty ports and have a name (like /dev/ttyUSB0, /dev/ttyUSB1, /dev/ttyACM0 etc, generalised as /dev/ttyUSBx or /dev/ttyACMx).

> [!NOTE]
> If you're curious, see [*What is the difference between /dev/ttyUSB and /dev/ttyACM?* from r/Linux](https://www.reddit.com/r/linux/comments/11y07qn/what_is_the_difference_between_devttyusb_and/)


# How to check where your device is connected?

1.  **Make sure that only one device (e.g. ESP32) is connected to your laptop.**

2.  **Check for `ttyUSBx` or `ttyACMx` ports in `/dev/` directory.**

    ```bash
    ll /dev/ttyUSB* /dev/ttyACM*
    ```

    You should see something like this:

    ```
    crw-rw---- 1 root dialout 188, 0 Jun  5 12:34 /dev/ttyACM0
    ```


# What if you are not able to program the device?

## Temporary solution:

1.  **Find out the exact port name of your device** (e.g. `/dev/ttyUSB0` or `/dev/ttyACM0`) using the command above.

2.  **Give yourself permission to program the device** using the following command:

    ```bash
    sudo chmod 777 /dev/ttyUSB0
    ```
    Replace `/dev/ttyUSB0` with the actual port name of your device.


## Permanent solution:

1.  **Add yourself to the `dialout` group** using the following command:

    ```bash
    sudo usermod -aG dialout $USER
    ```

2.  **Restart your computer** for the changes to take effect.

    ```bash
    sudo reboot now
    ```