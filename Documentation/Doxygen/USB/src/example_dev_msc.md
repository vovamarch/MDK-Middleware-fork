# USB Device Mass Storage {#dev_msc_tutorial}

This example implements a mass storage USB Device using \ref MSC.

The examples accesses on-chip RAM. The USB Host can then access the new drives using standard file access methods. The following picture shows an exemplary connection of the development board and the USB Host Computer.

![USB device mass storage example hardware setup](msc_dev_example_setup.png)

## Project Organization {#prj_org_dev_msc}

The USB Device MSC project is available as part of \ref usbd_ref_example "USB Device Reference example".

**Application Source Files**

 - `MassStorage.c`: contains the main C function that initializes the board hardware and the USB Device Component.
 - `MemoryDiskImage.c`: a FAT12 disk image with small README.TXT file that gets copied to the RAM disk.
 - `USBD_User_MSC_0.c`: adapted code template that implements necessary file access functions. Refer to \ref usbd_mscFunctions for details about these template functions.

**Software Components Configuration Files**

Configuration files for the software components used in the project are available in the `/RTE/` directory and can be modified by users to adjust the operation of related components. Section \ref usbd_rte_components gives an overview about the components and their dependencies.

Following configuration files are provided with this example:

 - For the USB component, in the `/RTE/USB/` folder:
   - `USBD_Config_MSC_0.h`: \ref usbd_mscFunctions_conf "USB Device MSC configuration"
   - `USBD_Config_0.h`: \ref usbd_coreFunctions_conf "USB Device Core configuration".
   - `USB_Debug.h`: \ref usbDevEvrConfig "USB Device Debug configuration".
 - For the CMSIS components, in the `/RTE/CMSIS/` folder:
   - `RTX_Config.h` and `RTX_Config.h`: [CMSIS-RTX Configuration files](https://arm-software.github.io/CMSIS-RTX/latest/config_rtx5.html) for the RTOS Kernel.

When a board layer is added to the project, corresponding configuration files for the board and device components will become available in the local `/RTE/` directory as well.

**Board Layer**

In order to build the USB Device HID project it needs to be extended with a compatible board layer that provides following CMSIS-Driver interfaces as [connections](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#connections):
 - `CMSIS_USB_Device`
 - `CMSIS_VIO`

## Build the Project {#prj_build_dev_msc}

Open the **USB Device** Reference Example and select **MSC** as an active project for the build process. Make sure the compatible board layer is configured.

Section [Working with MDK-Middleware Examples](../General/working_with_examples.html) explains in more details how to access, configure and build an MDK-Middleware example project for your target hardware.

## Run the Example {#prj_run_dev_msc}

**Hardware Setup**

Board-specific setup such as jumpers, USB ports, power supply, etc. are documented in the board layer description (`README.md`) of your selected target.

 - Load the firmware image to your development board.
 - Use a USB cable to connect your development board to the Host PC and power up your board.
 - Wait for the driver installation on the PC to complete.

**PC Software**

On a Windows PC you can test the example using the **Windows Explorer**. After a successful driver installation you can observe **USB_Memory** drive become available. On this drive you can find a single file `README.txt` with the following content:

```txt
This is a USB Memory Device Demonstration.
https://www.keil.com/pack/doc/MW/USB/html/dev_msc_tutorial.html
```
