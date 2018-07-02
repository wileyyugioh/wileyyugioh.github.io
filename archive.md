---
title: Archive
---

### Archive

<ul>
    {% for post in site.posts %}
    <li>
    {% assign d = page.date | date: "%-d" %} 
    {% assign m = page.date | date: "%B" %} 
    {% case m %}
        {% when 'April' or 'May' or 'June' or 'July' %}{{ m }}
        {% when 'September' %}Sept.
        {% else %}{{ page.date | date: "%b" }}.
    {% endcase %}
    {% case d %}
        {% when '1' or '21' or '31' %}{{ d }}st
        {% when '2' or '22' %}{{ d }}nd
        {% when '3' or '23' %}{{ d }}rd
        {% else %}{{ d }}th
    {% endcase %}, 
    {{ page.date | date: "%Y" }}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
</ul>
