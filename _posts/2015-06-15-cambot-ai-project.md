---
layout: post
title: "[DRAFT] Cambot AI project"
subtitle: 
author: matbaj
header-img: "img/post-bg-03.jpg"

---
#### WARNING: THIS IS STILL SKETCH ####
This is article about journay of creating interactive assistant in python.
Cambot is a project for AI course at University of Wroclaw.
It was created by [me](https://github.com/matbaj) and [Keicam](https://github.com/Keicam).
All Sources can be found [here](https://github.com/matbaj/cambot).

###Features###

This project is still in begining state and it has big possibility to evolve.
Current features that are implemented:

* It has interactive command line
* It can recognise voice
* It can say result of query
* check mails (reads unreaded mail snippets)
* check callendar (reads 10 next meetings)
* check weather
* control camera
* say yes/no with camera

###Preparation###

To build this project You will need:

* Arduino uno or nano
* Sony Eye Camera PS3
* Pan/Tilt Bracket (You can find it [here](https://www.sparkfun.com/products/10335))
* 2 servos

In my case I had one spare arduino and PS3 camera and I bought kit [here](http://botland.com.pl/chwytaki-i-uchwyty/2547-uchwyt-do-serw-micro-pantilt-serwa-dagu.html)

###Workspace Preparation###

We prefer to use linux as workspace OS because of reasons.
Software that You will need:

* Arduino IDE
* minicom(optional)
* python (we used 2.7)

We tested it on Arch linux and Ubuntu so it shouldn't be problem with only choosen one distro.



###Building stand###

First what You will need to do it will be setup Pan/Tilt Bracket.
Instruction is included in kit but in case You lost it or something happen You can find it [here](https://www.sparkfun.com/datasheets/Robotics/Other/sensor%20pan%20tilt%20manual.jpg)

Next step it will be connecting somehow camera to this stand.
I used zip straps to do this In way that is shown in picture below

![Camera stand](/img/article-cambot-camera.jpg)

After connecting camera You need to have stable stand.
In my case I used box from kit that I bought.
I made hole for servo on top of that box and I put inside Arduino uno (exactly it's equivalent).
Other cables You can put just like on this picture

![Box](/img/article-cambot-box.jpg)

Sketch for arduino You can find in repository at arduino/tilt.ino.
If You don't know how to upload arduino sketches I would prefer to send You to arduino getting started article.

Connecting pins to arduino:

|  Arduino      | destination   |
|:-------------:|:-------------:|
| VCC           | Servo 1 RED   |
| VCC           | Servo 2 RED   |
| GND           | Servo 1 BROWN |
| GND           | Servo 2 BROWN |
| PIN 9         | Servo 2 ORANGE|
| PIN 10        | Servo 1 ORANGE|

Where Servo 1 is the servo partially in box and it's for X axis and Servo 2 is Y axis


###Getting sources and running app###

You will need install:

* pywapi (arch: yaourt -S aur/python2-pywapi)
* SpeechRecognition (arch: pip2 install SpeechRecognition)
* httplib2 (arch: yaourt -S community/python2-httplib2)
* googleapiclient (arch: yaourt -S community/python2-google-api-python-client)
* dateutil (arch: yaourt -S community/python2-dateutil)
* opencv (arch: yaourt -S extra/opencv)
* numpy (arch: yaourt -S python2-numpy)
* pyaudio (arch: yaourt -S aur/python2-pyaudio)
* espeak (arch: yaourt -S espeak)

After You install this You will need create application on google dev website and download
json.
Better instruction You will find here:
["https://developers.google.com/api-client-library/python/start/get_started"](https://developers.google.com/api-client-library/python/start/get_started)
When You get this file. Put it in directory with project.

That's all. You should be able to run this application and have fun interacting with it :)
