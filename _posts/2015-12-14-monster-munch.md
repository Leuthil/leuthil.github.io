---
layout: game
title: Monster Munch
created: 2015-12-14
description: Ludum Dare 34 Jam Entry
image: /images/games/monstermunch/monstermunch1.JPG
banner: /images/games/monstermunch/monstermunch1.JPG
engine: Unity
platforms:
  - name: Unity Web Player
    url: http://leuthil.itch.io/monster-munch
url: http://ludumdare.com/compo/ludum-dare-34/?action=preview&uid=24714
thumbnail: http://ludumdare.com/compo/wp-content/compo2//511439/24714-shot0-1450151525.jpg-crop-180-140.jpg
media:
  - name:
    type: image
    url: /images/games/monstermunch/monstermunch4.gif
  - name:
    type: image
    url: /images/games/monstermunch/monstermunch1.JPG
  - name: 
    type: image
    url: /images/games/monstermunch/monstermunch2.JPG
  - name: 
    type: image
    url: /images/games/monstermunch/monstermunch3.JPG
thirdparty:
  - name: InControl
    url: http://www.gallantgames.com/pages/incontrol-introduction
---


You work at a food production facility but haven't eaten all day. Your boss leaves for 2 minutes so you take the opportunity to indulge and eat as much as you can. Production in this facility is not always perfect so be careful for hazards and mishaps!

## Development ##

In many games that utilize dual analog stick control schemes, one stick is usually dedicated to player movement. For this game I really wanted to explore the concept that each analog stick would control a separate limb to see how well players can focus on more than one thing at a time.

I began by first prototyping the limb movement using two analog sticks. This involved creating a basic form of inverse kinematics through Unity's physics engine. The arm is made up of different joints with specific angle limits to make the arm movement more realistic. Then when the player moves each analog stick, it applies physics forces to the hands in the desired direction and also applies some rotation.
