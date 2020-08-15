# Parameters

## Overview

All AvAnon nodes have some internal parameters which can be adjusted via the UAVCAN interface. Consult the page for each AvAnon device for details on each parameter.

## Changing parameters using UAVCAN GUI and SLCAN tool

1. Install the [UAVCAN GUI](https://github.com/UAVCAN/gui_tool)
2. Connect your [SLCAN tool](https://zubax.com/products/babel) to your computer
3. Open the UAVCAN GUI and select your SLCAN tool  

    ![UAVCAN GUI Connection Dialog](/images/CANGUI_Connect.png)

4. Set your local Node ID and click the "check" button

    ![UAVCAN GUI Set Local Node ID](/images/CANGUI_SetNodeID.png)

5. Connect your AvAnon node to your SLCAN tool
    * The node should appear in the GUI "Online Nodes" list

        ![UAVCAN GUI Node List](/images/CANGUI_NodeList.png)

6. Double-click on the AvAnon node
    * A window like this should appear
    
        ![UAVCAN GUI Node Properties](/images/CANGUI_NodeProps.png)

7. Under "Configuration Parameters, click on "Fetch All"

    ![UAVCAN GUI Node Properties](/images/CANGUI_ConfigControls_FetchAll.png)

8. The parameters will appear in the list below

    ![UAVCAN GUI Node List](/images/CANGUI_NodePropsParamsOnly.png)

9. Double-click on a parameter to open the param editor dialog

    ![UAVCAN GUI Node List](/images/CANGUI_ParamChange.png)

10. Change the parameter as desired, noting the displayed min and max values. Consult the page for each AvAnon device for details on each parameter.
11. Click on "Send" to send the new value to the node, then close the editor dialog
12. Repeat steps 9-11 for any other parameter changes
13. When done with all changes, select "Store All" to write the parameter changes to the device's nonvolatile memory

    ![UAVCAN GUI Node List](/images/CANGUI_ConfigControls_StoreAll.png)

14. You're done!