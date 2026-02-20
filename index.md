# Welcome to Our TOURCS Blog

This is our TORCS development blog.

### Team Members:
* Jimi Wilson
* Kerem Nur
* Hannah Krebs Rocha
* Lewis Beamond
* Oliver Holbourns
* Rhys Womack

---

### Weekly Logs:
<ul>
  {% for post in site.posts %}
    <li>
      {{ post.date | date: "%B %d, %Y" }} - <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> 
    </li>
  {% endfor %}
</ul>