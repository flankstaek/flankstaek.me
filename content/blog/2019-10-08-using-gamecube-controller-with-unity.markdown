---
categories: development
date: '2019-10-08T12:00:00Z'
keywords: unity gamecube controller gcc gc gamedev game development tutorial
tags: unity gamecube controller gamedev game development
title: How to use a Gamecube Controller with Unity
---
In most of my internet searching on this issue, I came across very little helpful information. This is my experience in trying to get a gamecube controller working with Unity. If you have a different experience or need help figuring something out, feel free to reach out to me at my [email](mailto:ian@flankstaek.me)

Anyway, lets get on with it.

Set Up
=========================

To start, you need to have an adapter plug your gamecube controller into your computer. If you're using some weird USB Gamecube Controller I don't know how to help you, I'm sorry. If you have an unofficial adapter (like me), you will have to follow [these](https://www.smashladder.com/guides/view/26oz/controller-guide-2-0#Using-Dolphin-s-Native-Support-Requires-an-actual-Nintendo-Switch-adapter-OR-a-3rd-adapter-with-a-toggle-on-it) instructions, if you have an official one it might work out of the box but I'm unsure. I'd recommend following [that](https://www.smashladder.com/guides/view/26oz/controller-guide-2-0#Using-Dolphin-s-Native-Support-Requires-an-actual-Nintendo-Switch-adapter-OR-a-3rd-adapter-with-a-toggle-on-it) link and installing Zadig to configure your controller to begin. In addition, if your Adapter has a toggle for "PC" and "Wii U", it must be set to "PC" in order to work with Unity, so if you are not getting any input from your controller that is a good thing to check.

Once you have installed the proper drivers and set up your controller, you're ready to open up Unity.

Project Settings
==========================

In your Unity project, go to Project Settings, and then Input and set up any additional axes that you'd like to use. There are two types of input we'll be setting up with our controller joystick axes and joystick buttons. For both types, Gravity, Dead, and Sensitivity do not seem to have any major effect, but let me know if you've found values that you think work best. You will want snap and invert off for these most likely, but frankly all of these options depend on the game you're making.

For joystick axes, your layout will look like this:
![Joystick Setup](/assets/images/joystick-setup.png)
For Joysticks you will be changing the "Axis" Dropdown to the value I give you.

For joystick buttons, your layout will look like this:
![Button Setup](/assets/images/button-setup.png)
You will be updating Positive or Negative Button to be equal to "joystick button X" where X is the value given.

Now that all of our axes are set up, these are the values I was able to discover for the different Gamecube Controller axes, and what they do. If you find any I missed, as there are several buttons I was not able to figure out, please let me know.


Axis Values
===============================
X Axis (1st Axis): X Axis on the Analog Stick <br/>
Y Axis (2nd Axis): Y Axis on the Analog Stick <br/>
3rd Axis: C-Stick Vertical <br/>
4th Axis: Nothing <br/>
5th Axis: Nothing <br/>
6th Axis: C-Stick Horizontal <br/>
7th Axis: D-Pad Horizontal <br/>
8th Axis: D-Pad Vertical <br/>

These are all of the axis values I found.

Button Values
===============================
Again, this is in the format "joystick button X" for the button value.

0: X <br/>
1: L+A or R+A <br/>
2: B <br/>
3: Y <br/>
4: L <br/>
5: R <br/>
6: None <br/>
7: Z <br/>
8: None <br/>
9: None <br/>
10: None <br/>
11: None <br/>
12: D-Pad Up <br/>
13: D-Pad Right <br/>
14: D-Pad Down <br/>
15: D-Pad Left <br/>

These are all of the button values I found.

That's All
=================
If you have any questions or concerns, or you find any different info on how to do this. Please reach out to me at my [email](mailto:ian@flankstaek.me). Hopefully this helps.