---
layout: game
title: Hoops Battle
created: 2017-11-15
description: Multiplayer Basketball Duels
image: /images/games/hoopsbattle/hoopsbattle1.jpg
banner: /images/games/hoopsbattle/hoopsbattle1.jpg
engine: Unity
platforms:
  - name: Android
    url: https://play.google.com/store/apps/details?id=ca.andrewbruno.hoopsbattle
url: https://play.google.com/store/apps/details?id=ca.andrewbruno.hoopsbattle
thumbnail: http://andrewbruno.ca/images/games/hoopsbattle/logo.png
media:
  - name:
    type: image
    url: /images/games/hoopsbattle/hoopsbattle-2p-gameplay.gif
  - name:
    type: image
    url: /images/games/hoopsbattle/hoopsbattle-menu-gameplay.gif
  - name: 
    type: image
    url: /images/games/hoopsbattle/hoopsbattle1.jpg
  - name: 
    type: image
    url: /images/games/hoopsbattle/hoopsbattle2.jpg
thirdparty:
  - name: Google Play Games plugin for Unity
    url: https://github.com/playgameservices/play-games-plugin-for-unity
---


Compete against your friends in the ultimate basketball hoop duel! This game is incomplete.

## Development ##

This game began as a project to give me experience developing a networked multiplayer game. It integrates with the [Google Play Games plugin for Unity](https://github.com/playgameservices/play-games-plugin-for-unity), which facilitates matchmaking and peer-to-peer communication.

Despite originating as a multiplayer learning experience, the game has evolved to include the following features:
- Quick online matchmaking
- Challenge a friend online
- Two player local play
- Compete against AI of varying difficulties

### Basketball ###

Before beginning work on the multiplayer component, I needed to actually implement a basketball throw and bounce mechanic that felt right. I started by integrating with Unity's mobile input system to create the basketball shoot mechanic. To generate the trajectory line, I used the Line Renderer component with a custom shader to create the moving dotted line effect. To ensure the basketball bounce felt realistic, I used various [basketball reference videos](https://www.youtube.com/watch?v=ZvgJ7mVxeg0) to ensure I had set the friction and bounce factor of the basketball just right.

### Design ###

As the target platform is mobile, I wanted to ensure that a duel was short enough to allow players to stop when they need to, but also be long enough to feel satisfying. Deciding that the optimal game length was relatively short, I wanted to keep player retention high by automatically putting the player into a new duel right after finishing a previous one. I was able to implement this for all game modes.

### Nothing but Net ###

I wanted specific gameplay elements to capture the same joy that real basketball can give you. One of the most satisfying aspects of basketball is the net's reaction to the ball going in. To accomplish this, I ended up adding in 3D elements - the net mesh utilizes the 3D Cloth component and a Skinned Mesh Renderer. Lastly, in order to have the 2D ball interact with the cloth renderer, I added a 3D collider to the ball.

### Multiplayer ###

Building multiplayer games for mobile can introduce challenges that other platforms do not deal with, such as very poor and unreliable network conditions, or bandwidth concerns. I had two main goals: ensure that the data usage per minute was very low, and ensure that poor network conditions would not result in choppy or ugly gameplay. I decided to use many best practices outlined by [Glenn Fielder](https://gafferongames.com). The best practices which were implemented include:
- Packet Sequencing - to handle out-of-order packets
- Snapshot Compression - to keep packet size low by bounding and quantizing position & rotation
- Jitter Buffer - to ensure that bad network conditions don't result in jittery gameplay
- Snapshot Interpolation - to ensure smooth ball movement despite a low tickrate