---
title: Archive
---

### Archive

<ul>
    {% for post in site.posts %}
    <li>
        {% include pretty_date.md date=post.date %}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
</ul>
