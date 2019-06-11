---
layout: game
title: Monster Munch
created: 2017-11-15
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

Compete against your friends in the ultimate basketball hoop duel! This game is incomplete.

## Development ##

This game began as a project to give me experience developing a networked multiplayer game. It integrates with the [Google Play Games plugin for Unity](https://github.com/playgameservices/play-games-plugin-for-unity), which facilitates matchmaking and peer-to-peer communication.

Despite originating as a multiplayer learning experience, the game has evolved to include the following features:
- Two player online duel with matchmaking
- Challenge a friend to an online duel
- Two player local duel
- Compete against AI

### Basketball ###

Before beginning work on the multiplayer component, I needed to actually implement a basketball throw and bounce mechanic that felt right. I started by integrating with Unity's mobile input system to create the basketball shoot mechanic. To generate the trajectory line, I used Unity's line renderer with a customer shader to create the dotted lined effect. To ensure the basketball bounce felt realistic, I used various [basketball reference videos](https://www.youtube.com/watch?v=ZvgJ7mVxeg0) to ensure I had set the friction and bounce factor of the basketball just right.

### Design ###

As the target platform is mobile, I wanted to ensure that a duel was short enough to allow players to stop when they need to, but also be long enough to feel satisfying. As these duels were very short, I wanted to keep player retention high by automatically putting the player into a new duel right after finishing a previous one. I was able to implement this for all game modes.

### Nothing but Net ###

I wanted specific gameplay elements to capture the same joy that real basketball can give you. One of the most satisfying aspects of basketball is the basketball mesh's reaction to the ball going in. To accomplish this, I ended up blending 3D with 2D, where the net mesh utilizes a cloth renderer. Lastly, in order to have the 2D ball interact with the cloth renderer, I added a 3D collider to the ball.

### Multiplayer ###

Building multiplayer games for mobile can introduce challenges that other platforms do not deal with, such as very poor and unreliable network conditions, or bandwidth concerns. I had two main goals: ensure that the data usage per minute was very low, and ensure that poor network conditions would not result in choppy or ugly gameplay. I decided to use many best practices outlined by [Glenn Fielder](https://gafferongames.com). The best practices which were implemented include:
- Packet Sequencing - to handle out-of-order packets
- Snapshot Compression - to keep packet size low by bounding and quantizing position & rotation
- Jitter Buffer - to ensure that bad network conditions don't result in jittery gameplay
- Snapshot Interpolation - to ensure smooth ball movement despite a low tickrate