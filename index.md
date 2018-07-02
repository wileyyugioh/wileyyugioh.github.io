---
title: Home
---

### Stuff I've done

- [birddb - a crowd-sourced database of birds (may be down if I run out of hosting credit)](https://birddb.wileyy.com)

- [NylonSock - a C++ networking library in the style of socket.io](https://github.com/wileyyugioh/NylonSock)

- [Osu-Touchpad - a tablet emulator for mobile devices using Node.js](https://github.com/wileyyugioh/Osu-Touchpad)

### Writeups I think are neat

<ul>
    {% for post in site.posts limit:5 %}
    <li>
    {% assign d = post.date | date: "%-d" %} 
    {% assign m = post.date | date: "%B" %} 
    {% case m %}
        {% when 'April' or 'May' or 'June' or 'July' %}{{ m }}
        {% when 'September' %}Sept.
        {% else %}{{ post.date | date: "%b" }}.
    {% endcase %}
    {% case d %}
        {% when '1' or '21' or '31' %}{{ d }}st
        {% when '2' or '22' %}{{ d }}nd
        {% when '3' or '23' %}{{ d }}rd
        {% else %}{{ d }}th
    {% endcase %}, 
    {{ post.date | date: "%Y" }}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
    <li>[**Archive**](archive.md)</li>
</ul>
