# ODFX Presets Manager for Houdini Indie
Extension node for OD Tools in Houdini for applying parameter values from JSON files
### Disclaimer: This repository is a user initiative and is not directly related to the [OD Tools](https://origamidigital.com/cart/) or its author.
![Screenshot](Screenshot.png)
This node is an extension for the paid third-party plugin for Houdini called OD Tools and requires its Python modules to work:
You can check the tools at the https://origamidigital.com/cart/:

OD Tools has a feature that allows saving all parameters of the specified nodes:

    1. Right Click on any node to call Context Menu
    2. Go to ODTools Parameters -> Save All Parms to Json
    3. Specify a name and a folder on disk to save json file (use absolute folder path to avoid saving errors)
    4. Press Accept
    
![gif1](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/9b444106-e896-489a-8220-3ee0d71640b8)

After that, you can restore parameters from the json file:

    1. Right Click on any node to call Context Menu
    2. Go to ODTools Parameters -> Import Parms from Json
    3. Specify a json file on disk
    4. Press Accept

![gif2](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/4477501b-6ecb-4fe3-a369-841c8013ef65)

One helpful feature of this tool is its ability to load parameters matched by name, even if the destination and source nodes are different; that means you can easily apply parameter values from one node to another, simplifying your workflow and saving time.

The node streamlines the process of importing parameters from the json file. 

So, you only need to set the path in the "Preset Folder" parameter, and the "Preset List" will be auto-populated by json files located in the folder.

![gif3](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/a530655f-5029-4063-bfe0-e520c4396d21)

The preset name will be converted from the file name by the following pattern:

    1. Replacing all underscore with space.
    2. Remove the ".json" extension.

Specify the "Destination node" into which the node will try to import parameters from the JSON file.

![gif8](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/c022c7aa-0a49-4517-8206-a371f1a8e562)

Select a preset in the "Presets List" and press "Apply" to import parameters.

![gif4](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/14a984f0-12e5-4e85-a4a8-371bb0112e5f)

Toggle "Auto Apply" to force the preset to be loaded when selecting the "Presets List" item. 

![gif5](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/4f5512dd-9f3a-4715-a816-bd95168ff3a9)

That may help you quickly iterate over presets, but don't forget to press "Apply" to toggle off the "Auto Apply" parameter to avoid unexpected rewriting of parameters on the destination node. 

![gif6](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/fd85ef7c-7123-4f4c-aeb4-13c6d04a20f7)

The "destination node" can be a node of any context.

![gif7](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/ae932697-ec2a-40ec-998c-306b9ee46fbc)

### Update 1.1

![GIF3](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/f9195e8c-abd2-4082-ac2b-5f0da221797e)

An "Apply All Presets" button allows you to apply all presets to their respective destination nodes with a single click. This is particularly useful for quickly setting up multiple nodes with predefined configurations.

A "Parameters Filter" parameter allows filtering of parameters to be imported from the JSON file. If this parameter is not empty, only the listed parameters will be applied to the destination node. 

A "Select Parameters" dialog shows a list of parameters available in the JSON file. You can easily select which parameters to include. The dialog pre-selects items already included in the "Parameters Filter."

![GIF2](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/e512de3e-0a87-4691-b4d7-06d0a4f51a87)

The "Open Select Parameters on Cursor" parameter controls the positioning of the "Select Parameters" dialog. When enabled, the dialog appears near the cursor position. Otherwise, it appears centered on the screen.

An "Edit" button allows you to open the selected JSON preset file in the default system editor for quick modifications.

![GIF1](https://github.com/Faitel/ODFX_Presets_Manager/assets/10779163/d93f9325-6dcc-4caf-9463-c2d4bff28448)

### Update 1.2

Fixed bug with the Select parameters panel and added a scroll bar for previewing selected parameters.

Parameters Filter now works similarly to Houdini's native filtering fields; it uses space " " for separation instead of comma "," sign, and you can use * and ^ for filtering.

Added "Enable Instance" toggle to include or exclude preset from loading by the Apply All Parameters button.

### Reference

The node based on the OD Tools Python code shared in discord by [Oliver Hotz](https://discord.com/channels/279443049069674496/625410894200832061/1244293453026693120):

```Python
from OD import shelftools
shelftools.nodeParmsFromJson([node], path_to_json_file)
```

## Parameters description:

Auto Apply:

    Automatically apply the preset when changed. If disabled, you need to manually apply the preset by pressing the apply button.

Presets:

    Select the preset file to load. This dropdown is populated based on the JSON files found in the specified presets folder.

Destination Node:

    Specify the destination node where the preset parameters will be applied. Enter the path to the node.

Presets Folder:

    Specify the folder containing the preset JSON files. This folder will be scanned to populate the presets dropdown menu.

Open Folder:

    Open the specified presets folder in the system file manager.
    
Parameters Filter:

    Specify the parameters to filter when importing from the JSON file. Only these parameters will be applied to the destination node.

Select Parameters:

    Open the dialog to select parameters to include in the "Parameters Filter".

Filter on Cursor:

    When enabled, the "Select Parameters" dialog appears near the cursor position. Otherwise, it appears centered on the screen.

Edit:

    Open the selected JSON preset file in the default system editor for modifications.

