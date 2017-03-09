---
layout: game
title: Monster Companion
description: You are taking your little pets out for a walk when suddenly dangerous red spike balls come out of nowhere! Try to stay alive as long as possible by any means necessary, even using your pets as a shield - you monster! But be careful, your pets will get upset if they get hurt or if you don't feed them and may work against you!
image: http://ludumdare.com/compo/wp-content/compo2/479518/24714-shot0-1440463434.jpg
engine: Unity
platforms:
  - name: WebGL
    url: http://leuthil.itch.io/monster-companion
  - name: Windows
    url: http://leuthil.itch.io/monster-companion
  - name: Android
    url: http://leuthil.itch.io/monster-companion
url: http://ludumdare.com/compo/ludum-dare-33/?action=preview&uid=24714
thumbnail: http://ludumdare.com/compo/wp-content/compo2//479518/24714-shot0-1440463434.jpg-crop-180-140.jpg
media:
  - name:
    type: image
    url: http://ludumdare.com/compo/wp-content/compo2/479518/24714-shot0-1440463434.jpg
  - name: 
    type: image
    url: http://ludumdare.com/compo/wp-content/compo2/479518/24714-shot1-1440463434.jpg
thirdparty:
  - name: InControl
    url: http://www.gallantgames.com/pages/incontrol-introduction
---

<div class="u-max-full-width">
  <div class="row">
    <div style="vertical-align:top" align="left" class="eight columns">
      <div class="row">
        <p>{{ page.description }}</p>
      </div>
      
      {% if page.platforms %}
      <div class="row">
        <span><strong>Platforms:</strong></span>
        <ul>
          {% for platform in page.platforms %}
          <li><a href="{{ platform.url }}">{{ platform.name }}</a></li>
          {% endfor %}
        </ul>
      </div>
      {% endif %}
      
      {% if page.engine %}
      <div class="row">
        <span>
          <strong>Engine:</strong>
          {% include engine.html engine=page.engine height=20 %}
        </span>
      </div>
      <br />
      {% endif %}
      
      {% if page.thirdparty %}
      <div class="row">
        <span><strong>Third Party Resources:</strong></span>
        <ul>
          {% for asset in page.thirdparty %}
          <li><a href="{{ asset.url }}">{{ asset.name }}</a></li>
          {% endfor %}
        </ul>
      </div>
      {% endif %}
    
    </div>
    
    <div style="vertical-align:top" align="right" class="four columns">
      {% include gallery.html media=page.media %}
    </div>
  </div>
  {% if content %}
  <div class="row">
    {{ content }}
  </div>
  {% endif %}
</div>
