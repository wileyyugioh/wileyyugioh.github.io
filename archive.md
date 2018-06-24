---
title: Archive
---

### Archive

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url }}">
        {% assign m = page.date | date: "%B" %}
        {% case m %}
            {% when 'April' or 'May' or 'June' or 'July' %}{{ m }}
            {% when 'September' %}Sept.
            {% else %}{{ page.date | date: "%b" }}.
        {% endcase %}
        : {{ post.title }}
    </a>
    </li>
  {% endfor %}
</ul>