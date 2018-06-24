---
title: Archive
---

### Archive

<ul>
  {% for post in site.posts %}
    {% assign m = page.date | date: "%B" %}
    {% case m %}
        {% when 'April' or 'May' or 'June' or 'July' %}{{ m }}
        {% when 'September' %}Sept.
        {% else %}{{ page.date | date: "%b" }}.
    {% endcase %}
    <li>
        <a href="{{ post.url }}">{{ m }} {{ post.date | date: "%-d, %Y" }}: {{ post.title }}
    </a>
    </li>
  {% endfor %}
</ul>