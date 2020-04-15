# Tracker Monitor
The [Tracker ACAP](https://github.com/pandosme/acaps/tree/master/tracker) publish motion trackers on MQTT.  This flow demonstrates how to visualiza these on a dashboard.


## Required Nodes
Additional nodes you need to install
- node-red-dashboard
- node-red-contrib-axis-camera

## Dashboard
Bounding boxes will appear on the static image.  As there is no video the data is completely anonymized.

- Green box shows where the object is first detected.
- The blue dots will show the object path
- Red box shows where the object was lost

You can refresh both the image and flush all bounding boxes.
![Dashboard](pictures/dashboard.jpeg)

## Flow
Copy and import the [flow](https://github.com/aintegration/flows/blob/master/fileupload/flow.json) to your Node-Red
![Flow](pictures/flow.jpeg)