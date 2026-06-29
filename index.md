---
layout: default
title: Home
---

# Welcome to Our TORCS Blog

This is our TORCS development blog.

---

### Weekly Logs:
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> 
    </li>
  {% endfor %}
</ul>

---
<div class="video-wrapper">

<iframe width="560" height="315" src="https://www.youtube.com/embed/TAAIgZqrP5Q?si=Gf9LnIM-BCQ2GppY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

<br>

<div class="video-wrapper">
<iframe width="560" height="315" src="https://www.youtube.com/embed/iJH3hW8m0gw?si=Px8pSEbPhhHtqOIG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>
<br>

<div class="video-wrapper">
<iframe width="560" height="315" src="https://www.youtube.com/embed/yTuPL_EheMs?si=8zfnFK41uHJ1awbd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>


<br>

<div class="video-wrapper">
<iframe width="560" height="315" src="https://www.youtube.com/embed/60JVCn-JgNA?si=eWWsN1bBDibKYQIs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

<style>
  .video-wrapper {
    width: 100%;
    max-width: 800px;
    margin-bottom: 2rem;
  }
  
  .video-wrapper iframe {
    width: 100%;
    height: auto;
    aspect-ratio: 16 / 9;
    border-radius: 8px;
  }
</style>


