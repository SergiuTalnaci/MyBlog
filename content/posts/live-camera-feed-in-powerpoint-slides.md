---
title: "Present live camera feed in PowerPoint slides over Teams or Zoom"
description: "Create amazing presentations where you can put yourself inside the presentation great for remote first jobs"
date: 2021-06-19T20:00:50+02:00
author: "Sergiu"
language: "English"
tags: ["OBS", "PowerPoint", "OnlineMeetings", "OnlineTalks", "software", "software engineering"]
categories: ["Remote Presentations"]
images: [{'src':'/obs-online-presentations-title.jpg', 'alt': 'Denmark in May', 'stretch': 'horizontal'}]
--- 

# STREAM Camera in PowerPoint 

## Necessary software to install

 * [OBS](https://obsproject.com/da/download)
 * [Obs websocket server](https://obsproject.com/forum/resources/obs-websocket-remote-control-obs-studio-from-websockets.466/)
 * [Powerpoint OBS scene switcher](https://github.com/SergiuTalnaci/PowerPointObsSceneSwitcher)


### OBS 
Install OBS from here: [Obs download link](https://obsproject.com/da/download)

### OBS websocket server
For websocket server, you can find the file by scrolling all the way down, Install [OBS websocket server](https://obsproject.com/forum/resources/obs-websocket-remote-control-obs-studio-from-websockets.466/) plugin from here: [Obs websocket server github releases](https://github.com/Palakis/obs-websocket/releases/tag/4.9.1). 
<img src="/obs-online-presentations/obs-websocket-github.jpg" />

Download the installer that matches your OS, or unzip the contents of the ZIP file into the folder where you installed OBS (C:\OBSINSTALLPATH\obsstudio). I recommend closing OBS before installing or unzipping the websocket server. Once installed open OBS again, in the top menu click on Tools -> WebSockets Server Settings. It should look like this: 

<img src="/obs-online-presentations/obs-websocket-server-settings-menu.jpg" /> 
Enable authentication and set a password you can remember and type later. We will need to input the password we set here in the Powerpoint OBS scene Switcher. 


We need the webserver extension to change the OBS scenes when we change our powerpoint slides. 

### Powerpoint OBS Scene Switcher

Clone or download the scene switcher code. I have included a built version of the program you can just run in the Compiled Executable folder. Otherwise you will need visual studio 2019 or newer to build and run the code. 


## Setup

### Video resolution
In the lower right side of the screen there is a Settings button, click it and it should show an option popup. Click on the Video tab in the popup window. Set Base (canvas) Resolution and Output (Scaled) Resolution to 1920x1080.

<img src="/obs-online-presentations/obs-video-settings.jpg" /> 

I picked 1920x1080 as a resolution because it is the largest audience who has this screen format. It also scales well to 720p or 1440p screens. For all the other high end devices, they probably run on a higher resolution that can comfortably view the stream at 1080p.

### Obs Scenes
After you install OBS, by default it will have 3 scenes, I chose the first "Scene" as the "base scene" where I've added my microphone and camera as sources. We will use this scene with all of our slides, as it is simply the camera and microphone.  
<img src="/obs-online-presentations/obs-scenes-menu.jpg" /> 

As you can see in the image below, I've added Scene and Display Capture, as input sources. We will need to do this for every slide where our green screen changes. Let's being by creating a Scene and name it Slide 0. Under sources click the "+" button and select Scene as a source. 
<img src="/obs-online-presentations/obs-base-scene-inputs.jpg" /> 

Now we need to set a chroma filter for our display capture, this will allow the layer beneath the top layer, in this case our "Scene" layer will be shown in places where we have the right color green.

1. Right click the "Display Capture" source.
1. Click on Filters.
1. In the popup settings window select the Chroma key effect filter, if it's missing add it from the '+' sign under Effect Filters.
1. Set the Key Color Type to Green and use a Similarity value of 360. 

<img src="/obs-online-presentations/obs-display-capture-chroma-key-settings-popup.jpg" /> 

Now that we have our Scenes settings in order, make sure that both the scene and the Display Capture are full screen on the preview canvas. In my case I see the desktop of the display capture surrounded by a red square which is the base "Scene" that contains the camera and microphone input.

With these 2 layers, in order OBS will now make the color green of our display capture "transparent" so our 2nd layer can be seen through the green.  

### Powerpoint Slides
In our PowerPoint slides we simply put green wherever we want to appear, for example this is my first slide. Note that I put a slide from the left side animation on my name card to make it look more modern and integrated. 

<img src="/obs-online-presentations/obs-powerpoint-green-screen-powerpoint.jpg" /> 

Another important sidenote, in PowerPoint <b>remember to add Slide 0 in the presenter comments</b>. The image below is how it looks like on OBS in my "Slide 0" scene. As you can see the non green part of the screen is on top of my camera input, or in other words, everything that is screen becomes transparent on the "Display Capture" source so we can see the scene "Scene" which is the Camera and Sound Capture. 

<img src="/obs-online-presentations/obs-with-powerpoint-before-starting-fullscreen-preview.jpg" /> 

#### Center yourself to the side of the screen

In this slide I want to place myself to the left side of the screen. To do this I made the powerpoint slide with a large green block on the left side. I've also added "Slide 2" in the presenter comments of this Power point slide. Now we need to setup Slide 2 scene in OBS.  

<img src="/obs-online-presentations/obs-powepoint-green-screen-in-slide.jpg" /> 

As usual we use the Display Capture Source and Scene source, but note that I dragged the scene with my mouse to the left. You can see the "Scene source" is moved to the left, so much left that the left part of it is out of the canvas and won't be seen or rendered. However this allows us to be in the center of “Scene” to while being on the left side of the Powerpoint screen. 

<img src="/obs-online-presentations/obs-powepoint-camera-in-slide.jpg" />

 ## OBS Powerpoint scene switcher
<img src="/obs-online-presentations/obs-powepoint-switcher-program-example.jpg" /> 


## Present in Microsoft Teams
* Virtual camera
* Share screen preview
Now for the fun part, presentations 

### Virtual camera
<img src="/obs-online-presentations/microsoft-teams-obs-virtual-camera.jpg" /> 
<img src="/obs-online-presentations/obs-start-virtual-camera-control.jpg" /> 
### Screen share 

<img src="/obs-online-presentations/obs-powerpoint-green-screen-sample.jpg" /> 

<img src="/obs-online-presentations/obs-with-powerpoint-fullscreen-projector-menu.jpg" /> 

<img src="/obs-online-presentations/microsoft-teams-share-fullscreen-window.jpg" /> 