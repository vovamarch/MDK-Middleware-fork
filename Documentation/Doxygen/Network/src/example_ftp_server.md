# FTP Server {#FTP_Server_Example}

This examples implements an FTP server on a device that allows you to manage files from a computer connected to the same network. The following picture shows an exemplary connection of the development board and a Computer.

![FTP server hardware setup](ftp_setup.png)

## Project Organization

The FTP Server project is available as part of the \ref nw_ref_example "Network Reference Example".

**Application Source Files**

 - `FTP_Server.c` contains the main C function that initializes the board hardware and the Network Component.

**Configuration Files for Software Components**

Configuration files for the software components used in the project are available in the `/RTE/` directory and can be modified by users to adjust the operation of related components. Section TBD gives an overview about the components and their dependencies.

Following configuration files are provided with this example:

 - For the Network component, in `/RTE/Network/` folder:
   - `Net_FTP_Server.h`: \ref using_ftp_server_conf "FTP Server configuration".
   - `Net_Config_TCP.h`: \ref using_network_sockets_tcp_conf "TCP Socket configuration".
   - `Net_Config_UDP.h`: \ref using_network_sockets_udp_conf "UDP Socket configuration".
   - `Net_Config_ETH_0.h`: \ref using_ethernet_interfaces_conf "Ethernet Interface configuration".
   - `Net_Config.h`: \ref nw_Network_Core "Network Core configuration".
   - `Net_Debug.h`: \ref netDebugConfig "Network Debug configuration".
 - For the File System component, in the `/RTE/File_System/` folder:
   - `FS_Config.h`:
   - `FS_Config_MC_0.h`:
   - `FS_Debug.h`:
 - For the CMSIS components, in the `/RTE/CMSIS/` folder:
   - `RTX_Config.h` and `RTX_Config.h`: [CMSIS-RTX Configuration files](https://arm-software.github.io/CMSIS-RTX/latest/config_rtx5.html) for the RTOS Kernel.

When a board layer is added to the project, corresponding configuration files for the board and device components will become available in the local `/RTE/` directory as well.


**Board Layer**

In order to build the FTP Server project it shall be extended with a compatible board layer that provides following CMSIS-Driver interfaces as [connections](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#connections):
 - `CMSIS_ETH`
 - `CMSIS_MCI`
 - `CMSIS_VIO`
 - `STDOUT`

## Build the Project

Open the **Network** Reference Example and select **FTP Server** as an active project for the build process. Make sure the compatible board layer is configured.

Section [Working with MDK-Middleware Examples](../General/working_with_examples.html) explains in more details how to access, configure and build an MDK-Middleware example project for your target hardware.

## Run the Example

**Hardware Setup**

Board-specific setup such as jumpers, Ethernet ports, power supply, etc. is documented in the board layer description (`README.md`) of your selected target.

 - Load the firmware image to your development board.
 - Use an Ethernet cable to connect your development board to the local area network. The PC is assumed to be already a member   of this LAN.
 - If your hardware supports it, insert a SD card into the SD card slot. This will be the data storage that you will have access to. Hardware that does not have a SD card interface will most probably use a RAM disk for FTP demonstration.

**PC Software**

To connect to the FTP server, all you need is a FTP client. On a Windows PC you can use the Command Prompt. Simply type `ftp my_host` (or the respective hostname that you have chosen in the `Net_Config.h` file). If you have a DCHP server in your network, it will automatically connect to the FTP server. You will be asked for a username and password combination. As for all network examples, this is "admin" (without the quotes) for the user and no password (you can change the defaults in the `Net_Config_FTP_Server.h` file). After a successful log in, you should see something like this:

![FTP server command line interface](ftp_server.png)
