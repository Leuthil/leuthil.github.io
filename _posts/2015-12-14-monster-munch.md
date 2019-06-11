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

You work at a food production facility but haven't eaten all day. Your boss leaves for 2 minutes so you take the opportunity to indulge and eat as much as you can. Production in this facility is not always perfect so be careful for hazards and mishaps! This game is designed to be played with a controller with two analog sticks and two triggers.

## Development ##

In many games that utilize dual analog stick control schemes, one stick is usually dedicated to player movement. For this game I really wanted to explore the concept that each analog stick would control a separate limb to see how well players can focus on more than one thing at a time.

### Limb Movement ###

I began by first prototyping the limb movement. This involved creating a basic form of inverse kinematics through Unity's physics engine. The arm is made up of different joints with specific angle limits to make the arm movement more realistic. When the player moves each analog stick, physics forces are applied to the hands to move and rotate toward the direction of the analog stick.

### Hand Interaction ###

When the limb movement felt right, I moved onto having the hands close when each respective trigger was pressed. I wanted the hands closing to be able to interact with objects, and this was accomplished by using physics raycasts. When a raycast detects a grabbable object, the grabbable object is simply parented to the monster's hand to follow it along. For the hand crank, I had to create a physics joint between the hand crank and the monster's hand to provide resistance to the player when they attempt to move away from the crank while still holding it.

### Wrapping Up ###

The last pieces involved putting it all together, such as randomly generating the sequence of which objects would come out on the conveyer belt, how often bombs and other hazards would occur, and the scoring scale as the monster grows.