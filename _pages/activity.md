---
title: "Last Activities"
permalink: /activity.html
layout: page
---

<ul>
  {% for activity in site.data.activities %}
    <li>
      <b>{{ activity.date }}</b>:
      {% if activity.url %}
        <a href="{{ activity.url }}">{{ activity.type }} ({% if activity.distance %}{{ activity.distance}} km{% else %}{{ activity.time }} h{% endif %})</a>
      {% else %}
        {{ activity.type }} ({% if activity.distance %}{{ activity.distance}} km{% else %}{{ activity.time }} min{% endif %})
      {% endif %}
    </li>
  {% endfor %}
</ul>