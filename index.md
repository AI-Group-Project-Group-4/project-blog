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
      {{ post.date | date: "%B %d, %Y" }} - <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> 
    </li>
  {% endfor %}
</ul>

---

### Current Fastest Lap Time: 1:32.30


<iframe width="560" height="315" src="https://www.youtube.com/embed/yTuPL_EheMs?si=8zfnFK41uHJ1awbd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<br>

<iframe width="560" height="315" src="https://www.youtube.com/embed/60JVCn-JgNA?si=eWWsN1bBDibKYQIs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


