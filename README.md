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
3. Install [ffmpeg](https://ffmpeg.org/) `brew install ffmpeg` once installed run : `ffmpeg` output should be :
    ffmpeg version 4.1.4 Copyright (c) 2000-2019 the FFmpeg developers
      built with Apple LLVM version 10.0.1 (clang-1001.0.46.4)
      configuration: --prefix=/usr/local/Cellar/ffmpeg/4.1.4_2 --enable-shared --enable-pthreads --enable-version3 --enable-avresample --cc=clang --host-cflags='-I/Library/Java/JavaVirtualMachines/adoptopenjdk-12.0.1.jdk/Contents/Home/include -I/Library/Java/JavaVirtualMachines/adoptopenjdk-12.0.1.jdk/Contents/Home/include/darwin' --host-ldflags= --enable-ffplay --enable-gnutls --enable-gpl --enable-libaom --enable-libbluray --enable-libmp3lame --enable-libopus --enable-librubberband --enable-libsnappy --enable-libtesseract --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-libxvid --enable-lzma --enable-libfontconfig --enable-libfreetype --enable-frei0r --enable-libass --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libopenjpeg --enable-librtmp --enable-libspeex --enable-videotoolbox --disable-libjack --disable-indev=jack --enable-libaom --enable-libsoxr
      libavutil      56. 22.100 / 56. 22.100
      libavcodec     58. 35.100 / 58. 35.100
      libavformat    58. 20.100 / 58. 20.100
      libavdevice    58.  5.100 / 58.  5.100
      libavfilter     7. 40.101 /  7. 40.101
      libavresample   4.  0.  0 /  4.  0.  0
      libswscale      5.  3.100 /  5.  3.100
      libswresample   3.  3.100 /  3.  3.100
      libpostproc    55.  3.100 / 55.  3.100
    Hyper fast Audio and Video encoder
    usage: ffmpeg \[options\] [[infile options] -i infile]... {[outfile options] outfile}...

 4. Train an object detection model  - you can follow [these instructions](https://github.com/cloud-annotations/training/) on how to do so. You should end up with a  `model_web` folder. 
 5. Copy your `mode_web` folder in the directory you installed node red 
 6. In the node-red directory make the following changes to the `settings.js` folder 
Search and un-comment out the following

     httpAdminRoot: '/editor',
     httpNodeRoot: '/api',
     httpStatic: '/Users/<homefolder>/.node-red',
7. Run Node-Red by running this command : `node-red` 
8. Go to `[http://127.0.0.1:1880/editor/](http://127.0.0.1:1880/editor/#flow/38da0bb9.896c44)` in your browser 
9. Import Tello-Drone [flow](https://github.com/pmmistry/ObjectDetection-Node-RED-VideoStream/blob/master/flows/tellodroneflow.json) 
10. Turn Tello Wifi on
11. Inject Command and then streamon in the flow

**Flow should look like :** 


![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569004106085_Screen+Shot+2019-09-20+at+2.27.21+PM.png)

12. In another tab , go to : `[http://127.0.0.1:1880/api/dashboard](http://127.0.0.1:1880/editor/#flow/38da0bb9.896c44)` 

**Output should look like :** 

![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569004381901_Screen+Shot+2019-09-20+at+2.32.28+PM.png)


You should see live streaming with tello drone such as here :
 `<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Object detection and live streaming with <a href="https://twitter.com/hashtag/tellodrone?src=hash&amp;ref_src=twsrc%5Etfw">#tellodrone</a> and <a href="https://twitter.com/NodeRED?ref_src=twsrc%5Etfw">@NodeRED</a> 🥳🥳 stay tuned for docs and tutorial! <a href="https://twitter.com/IBMDeveloper?ref_src=twsrc%5Etfw">@IBMDeveloper</a> <a href="https://t.co/eBVHlbMMoh">pic.twitter.com/eBVHlbMMoh</a></p>&mdash; Pooja Mistry (@poojamakes) <a href="https://twitter.com/poojamakes/status/1174800354560630790?ref_src=twsrc%5Etfw">September 19, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>`

## Steps To get started with [Raspberry Pi](https://www.ryzerobotics.com/tello) 

1 . Confirm you have Node-RED and ffmpeg installed on Raspberry Pi 

    - To confirm node-red --> open pi terminal and type `nod-red` you should see node-red run and point you to a browser session 
    - To confirm ffmpeg --> open pi terminal and type `ffmpeg` You should see :
    ffmpeg version 4.1.4 Copyright (c) 2000-2019 the FFmpeg developers
      built with Apple LLVM version 10.0.1 (clang-1001.0.46.4)
      configuration: --prefix=/usr/local/Cellar/ffmpeg/4.1.4_2 --enable-shared --enable-pthreads --enable-version3 --enable-avresample --cc=clang --host-cflags='-I/Library/Java/JavaVirtualMachines/adoptopenjdk-12.0.1.jdk/Contents/Home/include -I/Library/Java/JavaVirtualMachines/adoptopenjdk-12.0.1.jdk/Contents/Home/include/darwin' --host-ldflags= --enable-ffplay --enable-gnutls --enable-gpl --enable-libaom --enable-libbluray --enable-libmp3lame --enable-libopus --enable-librubberband --enable-libsnappy --enable-libtesseract --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-libxvid --enable-lzma --enable-libfontconfig --enable-libfreetype --enable-frei0r --enable-libass --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libopenjpeg --enable-librtmp --enable-libspeex --enable-videotoolbox --disable-libjack --disable-indev=jack --enable-libaom --enable-libsoxr
      libavutil      56. 22.100 / 56. 22.100
      libavcodec     58. 35.100 / 58. 35.100
      libavformat    58. 20.100 / 58. 20.100
      libavdevice    58.  5.100 / 58.  5.100
      libavfilter     7. 40.101 /  7. 40.101
      libavresample   4.  0.  0 /  4.  0.  0
      libswscale      5.  3.100 /  5.  3.100
      libswresample   3.  3.100 /  3.  3.100
      libpostproc    55.  3.100 / 55.  3.100
    Hyper fast Audio and Video encoder
    usage: ffmpeg \[options\] [[infile options] -i infile]... {[outfile options] outfile}...

2. If you don’t have ffmpeg installed follow [these instructions](https://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/) to install ffmpeg on pi

3. Train an object detection model  - you can follow [these instructions](https://github.com/cloud-annotations/training/) on how to do so. You should end up with a  `model_web` folder. 
4.  Copy your `mode_web` folder in the directory you installed node red 
5.  In the node-red directory make the following changes to the `settings.js` folder 

Search and un-comment out the following

     httpAdminRoot: '/editor',
     httpNodeRoot: '/api',
     httpStatic: '/Users/<homefolder>/.node-red',

6. Run Node-Red by running this command : `node-red` 

7. Import the Raspberry Pi [flow](https://github.com/pmmistry/ObjectDetection-Node-RED-VideoStream/blob/master/flows/raspberrypiflow.json) 

**Flow should look like this :** 

![](https://paper-attachments.dropbox.com/s_02031894C9508F7373D84C3A2DE154DAF4053A3E21718FB401B1C717EE61E346_1569004956153_Screen+Shot+2019-09-20+at+2.42.14+PM.png)

8. Deploy and in a different tab go to ``[http://127.0.0.1:1880/api/dashboard](http://127.0.0.1:1880/editor/#flow/38da0bb9.896c44)`` 

You should see video stream from Raspberry Pi along with object detection 🎉 

----------
If you are interested in just streaming  check out this repo : 

