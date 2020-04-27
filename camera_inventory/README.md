# Camera Inventory

When working with many cameras you need an inventory.  This flow allows you to use a dashboard to populate an inventory that is stored in the global context store.
If you add a lot of cameras it is recommeded to also import the flow [device_discovery](https://github.com/aintegration/flows/tree/master/device_discovery)

## Dashboard
![Dashboard](pictures/dashboard.PNG)

## Prerequisites

Before importing the flow you need to import the following nodes (Menu | Manage pallette | Install)
- node-red-dashboard
- node-red-contrib-axis-camera

You need to set the device credentials in the Axis Device Node before heading to the dashbaord.

You should enable persistant storage in Node-Red in order for your inventory to survice a reboot.
Open the file .node-red/settings.js in an editor and remove the comments (//) on each line of the following section in the file.
```
    contextStorage: {
        default: {
            module:"localfilesystem"
        },
    },
```
You need to restart Node-Red after changes.

## Flow
Copy and import the [flow](https://github.com/aintegration/flows/blob/master/camera_inventory/flow.json) to your Node-Red

Once imported you will see.
![Flow](pictures/flow.PNG)

# Usage
Use the dashboard to add cameras to inventory.

The inventory is stored in global context and accessed with `cameras = global.get("cameras")`.

When you want to use a camera in e.g. a function node, add the followng
```
cameras = global.get("cameras");
if(!cameras)
  return;  //No inventory
camera = cameras["THE CAMERA SERIAL NUMBER"]
```
If you need an array of cameras
```
list = [];
cameras = global.get("cameras");
if(!cameras)
  return;  //No inventory
for(var serial in cameras)
 list.push(cameras[serial])
```
For-Each-Camera, put the following in a function node
```
cameras = global.get("cameras");
if(!cameras)
  return;  //No inventory
for(var serial in cameras)
 node.send({payload:cameras[serial]})
//DO NOT return msg;
```
