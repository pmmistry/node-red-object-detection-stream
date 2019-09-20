# Object Detection on live Video Stream using Node-RED

This repository contains Node-RED flow examples that demonstrate how to detect objects using  video stream from either [DJI Tello Drone](https://www.ryzerobotics.com/tello) or a [Raspberry Pi](https://www.raspberrypi.org/) using the [Node-RED visual editor](http://nodered.org).

----------
## Introduction

Have you ever wanted to detect objects using live video stream ? Well if so this repo will show you how to get started. 

This example will be using the  [node-red-contrib-ffmpeg](https://flows.nodered.org/node/node-red-contrib-ffmpeg) node. This node allows users to stream video from either a tello drone or a raspberry pi. 

![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569003082191_Screen+Shot+2019-09-18+at+8.44.10+PM.png)


## Steps to get started with [Tello Drone](https://www.ryzerobotics.com/tello) 
 1. Install [Node-RED](https://github.com/johnwalicki/Node-RED-Tello-Control/blob/master/docs/PART2.md)
 2. Install [**node-red-contrib-ffmpeg**](https://flows.nodered.org/node/node-red-contrib-ffmpeg) : `npm install node-red-contrib-ffmpeg`
 3. Install [ffmpeg](https://ffmpeg.org/) `brew install ffmpeg` once installed run : `ffmpeg` 
 4. Train an object detection model  - you can follow [these instructions](https://github.com/cloud-annotations/training/) on how to do so. You should end up with a  `model_web` folder. 
 5. Copy your `mode_web` folder in the directory you installed node red 
 6. In the node-red directory make the following changes to the `settings.js` folder 
Search and un-comment out the following
    ``` 
     httpAdminRoot: '/editor',
     httpNodeRoot: '/api',
     httpStatic: '/Users/<homefolder>/.node-red',
     
     ```
     
 7. Run Node-Red by running this command : `node-red` 
 8. Go to `[http://127.0.0.1:1880/editor/](http://127.0.0.1:1880/editor/#flow/38da0bb9.896c44)` in your browser 
 9. Import Tello-Drone [flow](https://github.com/pmmistry/ObjectDetection-Node-RED-VideoStream/blob/master/flows/tellodroneflow.json) 
10. Turn Tello Wifi on
11. Inject Command and then streamon in the flow

**Flow should look like :** 

![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569004106085_Screen+Shot+2019-09-20+at+2.27.21+PM.png)

12. In another tab , go to : `http://127.0.0.1:1880/api/dashboard` 

**Output should look like :** 

![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569004381901_Screen+Shot+2019-09-20+at+2.32.28+PM.png)


You should see [live streaming with tello drone ](https://twitter.com/poojamakes/status/1174800354560630790)


## Steps To get started with [Raspberry Pi](https://www.raspberrypi.org/) 

1 . Confirm you have Node-RED and ffmpeg installed on Raspberry Pi 

    - To confirm node-red --> open pi terminal and type `nod-red` you should see node-red run and point you to a browser session 
    - To confirm ffmpeg --> open pi terminal and type `ffmpeg` 

2. If you don’t have ffmpeg installed follow [these instructions](https://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/) to install ffmpeg on pi

3. Train an object detection model  - you can follow [these instructions](https://github.com/cloud-annotations/training/) on how to do so. You should end up with a  `model_web` folder. 

4.  Copy your `mode_web` folder in the directory you installed node red 

5.  In the node-red directory make the following changes to the `settings.js` folder 

Search and un-comment out the following

    ``` httpAdminRoot: '/editor',
     httpNodeRoot: '/api',
     httpStatic: '/Users/<homefolder>/.node-red',```

6. Run Node-Red by running this command : `node-red` 

7. Import the Raspberry Pi [flow](https://github.com/pmmistry/ObjectDetection-Node-RED-VideoStream/blob/master/flows/raspberrypiflow.json) 

**Flow should look like this :** 

![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569004956153_Screen+Shot+2019-09-20+at+2.42.14+PM.png)

8. Deploy and in a different tab go to ``[http://127.0.0.1:1880/api/dashboard](http://127.0.0.1:1880/editor/#flow/38da0bb9.896c44)`` 

You should see video stream from Raspberry Pi along with object detection 🎉 




