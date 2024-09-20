# USB Host Keyboard {#host_hid_tutorial}

This example implements a USB Host device that receives data from a USB Device (Keyboard) using \ref HID.

The graphical LCD on the evaluation board is used to show the keyboard inputs. The following picture shows an exemplary connection of a development board and the USB Keyboard Computer.

![USB host keyboard example hardware setup](usbh_hid_setup.png)

## Project Organization {#prj_org_host_hid}

The USB Host Keyboard project is available as part of the \ref usbh_ref_example.

**Application Source Files**

 - `Keyboard.c`: contains the main C function that initializes the board hardware and the USB Host Component. It also reads the input from the attached keyboard.
 - `stdout_display.c`: retargets the function `stdout_putchar` to the function `GLCD_DrawChar` of the graphics display.

**Software Components Configuration Files**

Configuration files for the software components used in the project are available in the `\RTE\` directory and can be modified by users to adjust the operation of related components. Section \ref usbh_rte_components gives an overview about the components and their dependencies.

Following configuration files are provided with this example:

 - `\RTE\USB\USBH_Config_HID.h`: \ref usbh_hidFunctions_conf "USB Host HID Class configuration".
 - `\RTE\USB\USBH_Config_0.h`: \ref usbh_coreFunctions_conf "USB Host Core configuration".
 - `\RTE\USB\USB_Debug.h`: configuration for the level of debug events in the USB component (with Event Recorder). See \ref usbh_evr "USB Host:Debug Events".
 - `\RTE\CMSIS\RTX_Config.h` and `\RTE\CMSIS\RTX_Config.h`: [CMSIS-RTX Configuration files](https://arm-software.github.io/CMSIS-RTX/latest/config_rtx5.html) for the RTOS Kernel.

When a board layer is added to the project, corresponding configuration files for the board and device component will become available in the local `\RTE` directory as well.

**Board Layer**

In order to build the USB Device Host Keyboard project it shall be extended with a compatible board layer that provides following CMSIS-Driver interfaces as [connections](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#connections):
 - `CMSIS_USB_Host`

## Build the Project {#prj_build_host_hid}

ToDo: reference to the general flow

## Run the Example {#prj_run_host_hid}

Board-specific setup such as jumpers, USB ports, power supply, etc are documented in the board layer description (`README.md`) of your selected target.

- Connect a USB keyboard to one of the development board's USB connectors.
- After downloading the compiled firmware onto the board, you should be able to see something similar on the graphics display:

![USB host keyboard example output](usbh_keyboard_glcd.png)
