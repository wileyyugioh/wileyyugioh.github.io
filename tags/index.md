---
title: Tags
---

<div class="post">
<h1 class="rainbow rainbow-text-animated">Tags</h1>
<ul>
{% capture temptags %}
    {% for tag in site.tags %}
        {{ tag[1].size | plus: 1000 }}#{{ tag[0] }}#{{ tag[1].size }}
    {% endfor %}
{% endcapture %}
{% assign sortedtemptags = temptags | split:' ' | sort | reverse %}
{% for temptag in sortedtemptags %}
    {% assign tagitems = temptag | split: '#' %}
    {% capture tag_name %}{{ tagitems[1] }}{% endcapture %}
    <li><a href="{{ page.collection_url }}tags/{{ tag_name }}"><code style="white-space: nowrap;">{{ tag_name }}</code></a></li>
{% endfor %}
</ul>
</div>
