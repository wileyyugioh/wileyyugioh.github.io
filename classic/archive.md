---
title: Archive
---

<h3 class="rainbow rainbow-text-animated">Archive</h3>

<ul>
    {% for post in site.categories[page.category] %}
    <li>
        {% include pretty_date.md date=post.date %}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
</ul>
