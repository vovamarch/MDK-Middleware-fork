# USB Device Mass Storage {#dev_msc_tutorial}

This example implements a mass storage USB Device using \ref MSC.

The examples accesses on-chip RAM. The USB Host can then access the new drives using standard file access methods. The following picture shows an exemplary connection of the development board and the USB Host Computer.

![USB device mass storage example hardware setup](msc_dev_example_setup.png)

## Project Organization {#prj_org_dev_msc}

The USB Device MSC project is available as part of \ref usbd_ref_example.

**Application Source Files**

 - `MassStorage.c`: contains the main C function that initializes the board hardware and the USB Device Component.
 - `MemoryDiskImage.c`: a FAT12 disk image with small README.TXT file that gets copied to the RAM disk.
 - `USBD_User_MSC_0.c`: adapted code template that implements necessary file access functions. Refer to \ref usbd_mscFunctions for details about these template functions.

**Software Components Configuration Files**

 - `\RTE\USB\USBD_Config_MSC_0.h`: \ref usbd_mscFunctions_conf "USB Device MSC configuration"
 - `\RTE\USB\USBD_Config_0.h`: \ref usbd_coreFunctions_conf "USB Device Core configuration".
 - `\RTE\USB\USB_Debug.h`: configuration for the level of debug events in the USB component (with Event Recorder). See \ref usbd_evr "USB Device:Debug Events".
 - `\RTE\CMSIS\RTX_Config.h` and `\RTE\CMSIS\RTX_Config.h`: [CMSIS-RTX Configuration files](https://arm-software.github.io/CMSIS-RTX/latest/config_rtx5.html) for the RTOS Kernel.

When a board layer is added to the project, corresponding configuration files for the board and device component will become available in the local `\RTE` directory as well.

**Board Layer**

In order to build the USB Device HID project it needs to be extended with a compatible board layer that provides following CMSIS-Driver interfaces as [connections](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#connections):
 - `CMSIS_USB_Device`
 - `CMSIS_VIO`

## Build the Project {#prj_build_dev_msc}

ToDo: reference to the general flow

## Run the Example {#prj_run_dev_msc}

**Hardware Setup**

Board-specific setup such as jumpers, USB ports, power supply, etc. are documented in the board layer description (`README.md`) of your selected target.

 - Use a USB cable to connect your development board to the Host PC and power up your board.
 - Wait for the driver installation on the PC to complete.

**PC Software**

On a Windows PC you can test the example using the **Windows Explorer**. After a successful driver installation you can observe **USB_Memory** drive become available. On this drive you can find a single file `README.txt` with the following content:

```txt
This is a USB Memory Device Demonstration.
https://www.keil.com/pack/doc/MW/USB/html/dev_msc_tutorial.html
```
