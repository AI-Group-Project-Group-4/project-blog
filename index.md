# Welcome to Our Project Blog

This is the documentation and weekly dev log for our university project. 

### Team Members:
* [Your Name]
* [Teammate 2]
* [Teammate 3]

---

### Weekly Logs:
<ul>
  {% for post in site.posts %}
    <li>
      {{ post.date | date: "%B %d, %Y" }} - <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> 
    </li>
  {% endfor %}
</ul>