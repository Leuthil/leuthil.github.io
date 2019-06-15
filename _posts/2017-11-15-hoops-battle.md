---
layout: project
title: Hoops Battle
permalink: /projects/hoops-battle.html
created: 2017-11-15
description: Multiplayer Basketball Duels
image: /images/games/hoopsbattle/hoopsbattle1.jpg
banner: /images/games/hoopsbattle/hoopsbattle1.jpg
platforms:
  - name: Android
    url: https://play.google.com/store/apps/details?id=ca.andrewbruno.hoopsbattle
url: https://play.google.com/store/apps/details?id=ca.andrewbruno.hoopsbattle
thumbnail: http://andrewbruno.ca/images/games/hoopsbattle/logo.png
media:
  - name:
    type: image
    url: /images/games/hoopsbattle/hoopsbattle_gameplay.gif
  - name: 
    type: image
    url: /images/games/hoopsbattle/hoopsbattle1.jpg
  - name: 
    type: image
    url: /images/games/hoopsbattle/hoopsbattle2.jpg
thirdparty:
  - name: Unity
    url: https://unity.com/
  - name: Google Play Games plugin for Unity
    url: https://github.com/playgameservices/play-games-plugin-for-unity
---

Hoops Battle is an online or local 1v1 three pointer game. Challenge your friends or play against the world in the ultimate basketball hoop duel!

## Development ##

This game began as a project to give me experience developing a networked multiplayer game. It integrates with the [Google Play Games plugin for Unity](https://github.com/playgameservices/play-games-plugin-for-unity), which facilitates matchmaking and peer-to-peer communication through the Google Play Games service.

The game has evolved to include the following features:
- Quick online matchmaking
- Challenge a friend online
- Two player local play

### Basketball ###

Before beginning work on the multiplayer component, I needed to actually implement a basketball throw and bounce mechanic that felt right. I started by integrating with Unity's mobile input system to create the basketball shoot mechanic. To generate the trajectory line, I used the Line Renderer component with a custom shader to create the moving dotted line effect.

### Design ###

As the target platform is mobile, I wanted to ensure that a duel was short enough to allow players to stop when they need to, but also be long enough to feel satisfying. Deciding that the optimal game length should be relatively short, I also needed some mechanism to ensure that players stayed playing the game. To accomplish this, I made sure that when a match was finished, the game would automatically queue the player for their next match.

### Nothing but Net ###

I wanted specific gameplay elements to capture the same joy that real basketball can give you. One of the most satisfying aspects of basketball is the net's reaction to the ball going in. To accomplish this, I created the net's mesh with the Cloth and Skinned Mesh Renderer components. In order for the 2D ball to interact with the cloth simulation, I added a hidden 3D ball collider which follows the 2D ball.

### Multiplayer ###

Building multiplayer games for mobile can introduce challenges that other platforms do not deal with, such as very poor and unreliable network conditions, or bandwidth concerns. I had two main goals: ensure that the data usage per minute was very low, and ensure that poor network conditions would not result in choppy or ugly gameplay. I decided to use many best practices outlined by [Glenn Fielder](https://gafferongames.com). The best practices which were implemented include:
- Packet Sequencing - to handle out-of-order packets
- Snapshot Compression - to keep packet size low by bounding and quantizing ball positions & rotations
- Jitter Buffer - to ensure that bad network conditions don't result in jittery gameplay
- Snapshot Interpolation - to ensure smooth ball movement despite a low tickrate