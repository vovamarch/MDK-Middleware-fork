# BSD Client/Server {#BSD_Examples}

The BSD server and client examples implement BSD compliant communication.

BSD sockets are often used for network communication as they provide a well-defined API for exchanging data over the network by utilizing TCP and UDP sockets.

An exemplary setup could look like this:

![BSD example hardware setup](bsd_example_setup.png)

## Project Organization

The BSD Client and BSD Server projects are available as part of the \ref nw_ref_example "Network Reference Example".

**Application Source Files**

 - For the BSD Client example:
   - `BSD_Client.c`  contains the main C function that initializes the board hardware and the Network Component for the BSD client. It also contains the actual code that is used to communicate with the BSD server.
 - For the BSD Server example:
   - `BSD_Server.c` contains the main C function that initializes the board hardware and the Network Component for the BSD server. The server is waiting for a connection from a BSD client.

**Configuration Files for Software Components**

Configuration files for the software components used in the project are located in the `/RTE/` directory and can be modified by users to adjust the operation of related components. Section TBD gives an overview about the components and their dependencies.

Following configuration files are provided with this example:

 - For the Network component, in `/RTE/Network/` folder:
   - `Net_Config_BSD.h`: \ref using_network_sockets_bsd_conf "BSD Socket configuration".
   - `Net_Config_TCP.h`: \ref using_network_sockets_tcp_conf "TCP Socket configuration".
   - `Net_Config_UDP.h`: \ref using_network_sockets_udp_conf "UDP Socket configuration".
   - `Net_Config_ETH_0.h`: \ref using_ethernet_interfaces_conf "Ethernet Interface configuration".
   - `Net_Config.h`: \ref nw_Network_Core "Network Core configuration".
   - `Net_Debug.h`: \ref netDebugConfig "Network Debug configuration".
 - For the CMSIS components, in the `/RTE/CMSIS/` folder:
   - `RTX_Config.h` and `RTX_Config.h`: [CMSIS-RTX Configuration files](https://arm-software.github.io/CMSIS-RTX/latest/config_rtx5.html) for the RTOS Kernel.

When a board layer is added to the project, corresponding configuration files for the board and device components will become available in the local `/RTE/` directory as well.


**Board Layer**

In order to build the BSD Client or BSD Server project it shall be extended with a compatible board layer that provides following CMSIS-Driver interfaces as [connections](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#connections):
 - `CMSIS_ETH`
 - `CMSIS_VIO`
 - `STDOUT`

## Build the Project

Open the **Network** Reference Example and select **BSD Client** or **BSD Server** as an active project for the build process. Make sure the compatible board layer is configured.

Section [Working with MDK-Middleware Examples](../General/working_with_examples.html) explains in more details how to access, configure and build an MDK-Middleware example project for your target hardware.

## Run the Example

**Hardware Setup**

Board-specific setup such as jumpers, Ethernet ports, power supply, etc. is documented in the board layer description (`README.md`) of your selected target.

 - Load the firmware image to your development board.
 - Use an Ethernet cable to connect your development board to the local area network. The PC is assumed to be already a member of this LAN.

**PC Software**

To make it work, you need to setup two development boards within the same network: a BSD server and a BSD client.

To test the BSD Server example stand-alone, run the Windows application *LEDSwitch.exe* that is available as part of [Keil MDK uVision](https://developer.arm.com/documentation/101407/latest/About-uVision/Installation) and is located in `<install_dir>\ARM\Utilities\LEDSWitch\Release\` folder, where `<install_dir>` refers to the Keil MDK uVision installation directory. The program runs stand-alone without installation.

Type in the IP address of your development board (IPv4 and IPv6 addresses are accepted). When connected, you can control the on-board LEDs.

![LED Switch Application](ledswitch.png)
