# Virtual Production Projects For Unreal Engine

This repository was recently rebuilt to hold multiple Unreal Engine example projects. Please let me know if this causes you any problems.  Worst case some files and directories may have been moved, hopefully you will just have to re-open them in the Unreal launcher and everything will be ok (at least, it was for me).

[![Virtual Production](http://img.youtube.com/vi/a3jh6HootAk/0.jpg)](https://www.youtube.com/watch?v=a3jh6HootAk "Virtual Production")

# Before you start

These projects all require some kind of VR tracking gear, a video capture devices and a camera.  Because everyone's hardware setup will be a little different most of them WILL require some modifications before they will work for you.  I have tutorials on Youtube that describe how to do this.  If you have never used Unreal Engine before it will make things easier if you take a couple of getting started courses on the [Unreal Engine Learning Hub](https://www.unrealengine.com/en-US/onlinelearning-courses) just to get familiar with Unreal's user interface.

Most of these examples assume you have a HTC Vive or Valve VR system with controllers, at least one base station and at least one tracking puck. All my tutorials assume you have this basic setup.  It is possible to use other configurations that cost less, but it will require more work to get everything setup.  

# In This Repository

* UE4VirtualProduction -- my original example which composites a live camera with a virtual set
* TrackerTest -- a project that measures tracker jitter and reports it.

# What you need to get started

Each of the examples has slightly different requirements, see their individual readme files for more details, but in general to get started doing Virtual Production you will need a Windows PC with a good graphics card. a way to get video into Unreal and a a solid color background (usually green or blue).  You may also need some lights or a good source of natural light.  A lot of these things are covered in more detail by the tutorials on [my youtube channel](https://www.youtube.com/user/GregCorson)

# Goals of this project

The purpose of this project is to figure out how Virtual Production can be made easy and cheap enough so more people can use it.  Sometimes I will be using more expensive hardware because nothing cheaper is available (yet) but I will always be looking for low cost alternatives to make it more affordable.  It is already possible to do some basic virtual production with just a PC and a webcam and there are many on-line communities full of people working on making this easier and cheaper for all kinds of uses.

# UNDER CONSTRUCTION

I'm in the process of reorganizing this repository so it can handle multiple examples. The information below will be organized into different directories in the near future.

# UE4VirtualProduction example

This is an example of a Virtual set where live green-screen video of your "talent" (actors) is composited with a 3d virtual set rendered in realtime by Unreal.  Features of the example include:

* A live video camera that is tracked so you can move it (even handheld)
* A tracked object (a cartoon hammer) you can make follow a tracker in the talent's hand
* A marker you can move to anyplace in the level you want the talent to stand.
* A tracked matte that prevents objects outside the green screen area from being seen, even if the camera moves.
* A way to delay the tracking data to keep it in sync with the live video
* A setup using Unreal's "composure" plugin to composite all the layers together.
* Foreground and Background layers in the composite so objects can appear in front of and behind the talent.

To avoid content licensing issues and keep the example small, only Unreal "starter content" from the 3rd person project template is used. In a few minutes you can migrate the assets from this project into any Unreal level you want to use as a virtual set.  See [how to migrate to your own project](./ReadMe_2.md) for instructions.  The Unreal "Virtual Studio" example has several TV studio levels that work well with this, the video above is one of them, find it on the Epic launcher under "learn".

# Documentation is on Youtube

See [my youtube channel](https://www.youtube.com/user/GregCorson) for documentation, tutorials, demos and tips on Virtual Production. There are also playlists with a lot of Virtual Production and mixed reality videos from other creators.

This may look complicated but you can get some great results from a very simple setup and since everything here runs in real-time, you can even use this setup for livestreaming!

# Please Help Out!

This example will get you started, but there is a lot of room for improvement.  There are still some issues with color correction of the live video, having the talent cast shadows and making the camera calibration easier just to name a few!  If you run into problems or have suggestions please feel free to contact me through "issues" here on Github or though my YouTube channel.

# Hardware Required

The only thing really required to do Virtual Production is an Unreal compatible camera & video capture card or a Webcam.  To use all the features and have a camera you can move, you need some kind of tracking system.  This can be a VR headset and it's controllers or specialized tracking devices.  The example is configured for the hardware and video studio I currently use so if your setup is different you will have to make some changes.

My setup is:
* A 35mm full frame consumer camera with HDMI out on a good tripod
* AJA Kona-HDMI 4 input HDMI capture card
* A Vive Pro VR setup (second generation base stations)
* Several Vive tracking pucks (second generation)
* Standard PC
* NVIDIA 2080 graphics card
* A large fabric green-screen and some lights

# New Steam input system in Unreal 4.24 or higher!

Starting with Unreal 4.24 and the latest Steam, you need to assign "roles" to each tracker and setup an input mapping for them to work. These are the steps I used to get it working, let me know if there is a better way.

* In steam's "manage trackers" assign a different "role" to each of your trackers such as "camera" and "keyboard"
* In Unreal Editor's "SteamVR Input" menu select "Launch SteamVr Bindings dashboard"
* Click on the controller icon and choose the role you assigned to your camera tracker
* Add an action that maps the raw pose to Special_1
* Repeat for your second tracker and assign to Special_2

