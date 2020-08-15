# Firmware Update

## Overview

The firmware on all AvAnon UAVCAN nodes can be updated via their UAVCAN interface. Make sure to keep your devices updated for the best performance!

## Updating using UAVCAN GUI and SLCAN tool

1. Download the latest firmware for your AvAnon node, save it somewhere accessible on your computer, and unzip the folder.
2. Install the [UAVCAN GUI](https://github.com/UAVCAN/gui_tool)
3. Connect your [SLCAN tool](https://zubax.com/products/babel) to your computer
4. Open the UAVCAN GUI and select your SLCAN tool

   ![UAVCAN GUI Connection Dialog](../.gitbook/assets/CANGUI_Connect%20%281%29.png)  

5. Set your local Node ID and click the "check" button

   ![UAVCAN GUI Set Local Node ID](../.gitbook/assets/CANGUI_SetNodeID.png)  

6. Connect your AvAnon node to your SLCAN tool
   * The node should appear in the GUI "Online Nodes" list

     ![UAVCAN GUI Node List](../.gitbook/assets/CANGUI_NodeList%20%281%29.png)  
7. Double-click on the AvAnon node you want to update
   * A window like this should appear

     ![UAVCAN GUI Node Properties](../.gitbook/assets/CANGUI_NodeProps%20%281%29.png)  
8. Click on "Update Firmware"

   ![UAVCAN GUI Node Properties](../.gitbook/assets/CANGUI_FWUpdate.png)  


   * You may get a warning that no dynamic ID server is running that asks if you want to continue. Select "yes".

9. Navigate to the AvAnon firmware file you downloaded earlier and select "open"

   **Warning** Make sure you select the correct firmware file for this node! Using this method, there is no protection against flashing firmware for the wrong node.

10. Sit back and wait!
    * You should see the node "Mode" switch to "SOFTWARE UPDATE"
    * The LED's on your AvAnon node should flash yellow/red alternately
    * Periodically, updates will appear in the GUI "Log Messages" box showing download progress
11. When the firmware update is successful, the node will restart
    * The displayed "Mode" will return to operational
    * The node's LED will flash green

      **Note** Some devices \(like the GNSS\) may not restart cleanly and the LED may flash red. If this happens, disconnect and reconnect the node. It should start up normally.
12. Verify the expected version is displayed next to "Software Version"

## Updating automatically using PX4-based autopilots

**Note** This guide has not been extensively tested. Please refer to PX4 documentation if you have trouble.

1. Download the latest firmware for your AvAnon node, save it somewhere accessible on your computer, and unzip the folder.
2. Ensure your autopilot's "UAVCAN\_ENABLE" parameter is set to 1 or higher
3. Insert your autopilot's SD card into your computer and navigate to it
4. Navigate to the firmware you saved and copy the folder named "com.AvAnon._nodename_" . You will paste this soon.
5. Navigate to the "fw" folder on the root of the card
   * If none exists, create it
6. Paste the firmware folder here
7. If you have multiple nodes to update, repeat this process, placing the firmware folders for each node type into the "fw" directory
8. Safely eject your SD card and insert it into your autopilot
9. Connect all nodes to be updated to your autopilot per their wiring instructions \(simply use the CAN interconnect cables\)
10. Power on your autopilot and wait!
    * The LED's on your AvAnon nodes should flash yellow/red alternately as they are being updated
11. When the firmware update is successful on each node, that node will restart and its LED will flash green

