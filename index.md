---
title: Home
---

<h3 class="rainbow rainbow-text-animated">Posts</h3>

<ul>
    {% for post in site.categories[page.category] limit:5 %}
    <li>
        {% include pretty_date.md date=post.date %}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
    <li><a href="{{ page.collection_url }}archive"><strong>Archive</strong></a></li>
</ul>

<h3 class="rainbow rainbow-text-animated">About Me</h3>

- My name is Wiley Yu.
- I have unironically caused significant harm to the international anime community.
- I can sometimes cook a French omelette.
- I never update this blog.