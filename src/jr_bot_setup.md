# Install VS Code

1.  Complete the [Post Ubuntu Installation Setup](setup_ubuntu.md) steps.

2.  Visit the [VS Code download page](https://code.visualstudio.com/Download) and download the `.deb` package for Ubuntu. Note the download location (usually `~/Downloads`).

3.  Open a terminal and navigate to the download location. For example, if the file is in `~/Downloads`, run:

    ```bash
    cd ~/Downloads
    ```

4.  Install the downloaded package using the following command:

    ```bash
    sudo apt install ./code_*.deb
    ```

> [!TIP]
> You may find it useful to be mindful of profiles in VS Code to avoid cluttering your editor. Learn more: https://code.visualstudio.com/docs/configure/profiles


# Install VS Code Extensions

We only need two VS Code extensions:

1.  **PlatformIO IDE**: This extension is required for building and uploading code to the ESP32 microcontroller. It also provides a convenient interface for managing libraries and dependencies. [Learn more](https://platformio.org/).

2.  **Dev Containers**: This extension allows you to develop inside a containerized [Docker](https://www.docker.com/) environment, which is useful for ensuring that your development environment is consistent across different machines. [Learn more](https://code.visualstudio.com/docs/devcontainers/containers).


## Installation

1.  Open VS Code.

2.  Go to the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of the window or by pressing `Ctrl+Shift+X`.

3.  Search for "PlatformIO IDE" (ID `platformio.platformio-ide`) in the Extensions Marketplace and click "Install".

4.  Search for "Dev Containers" (ID `ms-vscode-remote.remote-containers`) in the Extensions Marketplace and click "Install".

5.  Restart VS Code to ensure that the extensions are properly loaded.


# Download JR Bot Code and the Docker image

1.  Open a terminal and download the Docker image for the JR Bot project using the following command:

    ```bash
    docker pull ghcr.io/jr-ros/jr_bot_host:amd64-v1.1.1
    ```

> [!TIP]
> This download takes time, so you can do other things while it is running.

2.  Create or change to the folder where you want to store JR Bot's code. For example, to create a folder named `jr_bot` in your home directory and change to it, run:

    ```bash
    mkdir -p ~/jr_bot
    cd ~/jr_bot
    ```

3.  Download the ESP32 firmware.

    ```bash
    git clone https://github.com/JR-ROS/jr_bot_firmware.git
    ```

4.  Download the ROS2 code.

    ```bash
    git clone --recurse-submodules https://github.com/JR-ROS/jr_bot_ros.git
    ```

# Open and upload the firmware code to the ESP32

1.  Open the firmware project using VS Code. Replace `<path/to/your/jr_bot_firmware/>` with the actual path to the `jr_bot_firmware` folder you cloned in the previous step.

    ```bash
    code <path/to/your/jr_bot_firmware/>
    ```

    For example, if you cloned it into `~/jr_bot/jr_bot_firmware`, run:

    ```bash
    code ~/jr_bot/jr_bot_firmware
    ```

2.  Let PlatformIO finish installing the required libraries and dependencies. This may take a few minutes.

3.  Connect the ESP32 to your computer using a USB cable.

4.  Make sure your USB port is accessible and known. See the [USB Guide](usb.md).

5.  Press `Ctrl+Shift+P` to open the Command Palette, then type and select **PlatformIO: Upload** to compile and upload the firmware to the ESP32.


# Open the ROS2 code in a Dev Container

1.  Open the ROS2 project using VS Code. Replace `<path/to/your/jr_bot_ros/>` with the actual path to the `jr_bot_ros` folder you cloned in the previous step.

    ```bash
    code <path/to/your/jr_bot_ros/>
    ```

    For example, if you cloned it into `~/jr_bot/jr_bot_ros`, run:

    ```bash
    code ~/jr_bot/jr_bot_ros
    ```

2.  When prompted, click **Reopen in Container** to open the project in a Dev Container. This will ensure that you have a consistent development environment with all the necessary dependencies installed.

> [!TIP]
> If you are not prompted, you can manually reopen the project in a Dev Container by pressing `Ctrl+Shift+P`, typing **Dev Containers: Reopen in Container**, and selecting it from the list.

3.  When prompted, choose **Host PC** as the target for the Dev Container.

> [!INFO]
> The other option **SBC** is for running the code on a single-board computer (SBC) like a Raspberry Pi.

4.  Wait for the Dev Container to build and start. This may take a few minutes, especially the first time you open it.

5.  Once the Dev Container is running, you can start developing and testing your ROS2 code. You can use the integrated terminal in VS Code to run ROS2 commands and launch files.

    You can open a terminal in VS Code by pressing **Ctrl+\`** (backtick) or by going to **View > Terminal** in the menu bar.

    See the [JR Bot ROS README](https://github.com/JR-ROS/jr_bot_ros/blob/main/README.md) for more information on how to use the ROS2 code and launch files.