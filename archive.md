---
title: Archive
---

<h1 class="rainbow rainbow-text-animated">Archive</h1>

<ul>
    {% for post in site.categories[page.category] %}
    <li>
        {% include pretty_date.md date=post.date %}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
</ul>
