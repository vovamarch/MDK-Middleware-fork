# USB Host Mass Storage {#host_msc_tutorial}

This examples implemens a USB Host device that accesses a USB Mass Storage Device (USB memory stick) using \ref MSC.

This example will create or overwrite a `Test.txt` file on the connected USB Stick with the content "USB Host Mass Storage!".

The following picture shows an exemplary connection of the development board and an USB memory stick.

![USB host mass storage example hardware setup](usbh_msc_setup.png)

## Project Organization {#prj_org_host_msc}

The USB Host Mass Storage project is available as part of the \ref usbh_ref_example.

**Application Source Files**

 - `MassStorage.c`: contains the main C function that initializes the board hardware, the flash storage device and the USB Host Component. Also, it contains that code that will write a file with a message onto the attached USB stick.
 - `USBH_MSC.c` and `USBH_MSC.h`: adapted code template for the application specific functionality of the USB Host MSC class. It implements the access to a USB storage device and allows file I/O via the File System component.

**Software Components Configuration Files**

 - `\RTE\USB\USBD_Config_MSC_0.h`: \ref usbh_mscFunctions_conf "USB Host MSC configuration"
 - `\RTE\USB\USBH_Config_0.h`: \ref usbh_coreFunctions_conf "USB Host Core configuration".
 - `\RTE\USB\USB_Debug.h`: configuration for the level of debug events in the USB component (with Event Recorder). See \ref usbh_evr "USB Host:Debug Events".
 - `\RTE\File_System\FS_Config.h`:
 - `\RTE\File_System\FS_Config_USB_0.h`:
 - `\RTE\File_System\FS_Debug.h`:
 - `\RTE\CMSIS\RTX_Config.h` and `\RTE\CMSIS\RTX_Config.h`: [CMSIS-RTX Configuration files](https://arm-software.github.io/CMSIS-RTX/latest/config_rtx5.html) for the RTOS Kernel.

When a board layer is added to the project, corresponding configuration files for the board and device component will become available in the local `\RTE` directory as well.

**Board Layer**

In order to build the USB Device HID project it needs to be extended with a compatible board layer that provides following CMSIS-Driver interfaces as [connections](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#connections):
 - `CMSIS_USB_Host`

## Build the Project {#prj_build_host_msc}

ToDo: reference to the general flow

## Run the Example {#prj_run_dev_msc}

Board-specific hardware setup such as jumpers, USB ports, power supply, etc. are documented in the board layer description (`README.md`) of your selected target.

- Insert a USB memory stick to one of the development board's USB connectors and run the program.
- Detach the USB memory stick and attach it to a PC to check the availability of the `Test.txt` file.
