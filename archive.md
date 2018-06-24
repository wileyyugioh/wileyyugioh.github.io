---
title: Archive
---

### Archive

<ul>
    {% for post in site.posts %}
    {% assign temp = post.date | date: "%B" %}
    {% case temp %}
        {% when 'April' or 'May' or 'June' or 'July' %}{% assign m = temp %}
        {% when 'September' %}{% assign m = "Sept." %}
        {% else %}{% assign m = post.date | date: "%b" %}.
    {% endcase %}
    <li>
        <a href="{{ post.url }}">{{ m }} {{ post.date | date: "%-d, %Y" }}: {{ post.title }}
    </a>
    </li>
    {% endfor %}
</ul>