# Using Middleware Examples

## Explore Examples


## Prerequisites

 - Keil Studio, see [Install Keil Studio](https://developer.arm.com/documentation/109350/latest/Installation/Installing-Keil-Studio?lang=en#md298-installing-keil-studio__keil-studio-installation).
 - Hardware board supported by the target example project see 
 - Following CMSIS packs installed in the Keil Studio
   - Install MDK-Middleware pack
   - Install DFP and BSP packs for your target board
 - [Optional] Install uVision for Windows

## Open MDK-Middleware example

 - Follow the steps described in [Create a new solution](https://developer.arm.com/documentation/108029/latest/Arm-CMSIS-Solution-extension/Create-a-solution).
 - Expand the drop-down list **Templates. Reference Applications, and Examples** and in the **Reference Examples** group select a target MDK-Middleware application. Note, that not all listed application may be supported by your target hardware out of the box. So crosscheck with TBD  . Here is an example view:

## Build the project
 - Open the **Manage Solution** view 
   - In  the **Active Projects** area select the project(s) that should be used for build.
  - In the **Run and Debug ** area select the Run and Debug configurations.
  
 - Build the application for the selected target and observe in the output that no errors are present.

## Run and debug

 - [Connect your board](https://developer.arm.com/documentation/108029/0000/Get-started-with-an-example-project/Connect-your-board)
 - [Load the firmware to your board](https://developer.arm.com/documentation/108029/0000/Get-started-with-an-example-project/Run-the-solution-on-your-board) 
 - [Start a debug session in VS Code](https://developer.arm.com/documentation/108029/0000/Get-started-with-an-example-project/Start-a-debug-session)


### Debug from uVision

This section shows how to call the uVision Debugger from VS Code and use the advanced debug features such as Event Recorder and Component Viewer to analyse the MDK-Middleware.

## Using uVision IDE

This section explains how to create applications using the uVision IDE.

## Import examples
