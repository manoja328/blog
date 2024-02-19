---
layout: post
title:  "ball and beam system"
excerpt: ball and beam system with real-time image processing
comments: true
date:   2014-10-14 19:26:37 +0545
categories: hardware 
---

This project is a "ball and/On Beam" system.So this project is basically a PID controlled system where you
have a linear beam or 1D surface ( can be extended to a plane /2D) and you have to balance a ball that is
in motion at any position of the beam desired by the user.Now there are various methods to give that "desired position"
some use potentiometer converted to a distance (by doing ADC mapping) etc. We used a simple hand gesture to set the ball's
position on the beam which is found out using image processing. We take a colored ball and using HSV threshold and 
some "moments" calculation we find the center of the ball.



![png](/assets/ballbeam/thr.png)

![png](/assets/ballbeam/2.png)


My setup had following things:

  1. A laptop with webcam
  2. A PIC microcontroller (PIC16f877a)
  3. A USB to Serial module
  4. A ball and beam setup.
  
I actually implemented this algorithm in my laptop using a python script which you can find at the end of the the post
The beam is a cheap wire-cover having a little groove enouhg for a round tennis ball to move in a straight path. 
It is attached to a fixed support and is moved about the mean position with a Servo motor attached to it.
The servo is controlled by a PIC microcontroller and the extent of movement is actually send from my
laptop to PIC serially via a USB-Serial module .The data sent from PC is the angle with which the servo has 
to move, which is determined by calculating the position of ball and  the setpoint. PID control is used for providing
control feedback to the whole system. All the PIC does is change that angle into appropriate electrical signal to drive
the servo meter.

[Video link](https://www.youtube.com/watch?v=cayVlMbv05g&feature=youtu.be%20)

[Code](https://drive.google.com/file/d/0B3wAJh9-HvDcM1NaRmt2VVlOZlU/view?usp=sharing)

