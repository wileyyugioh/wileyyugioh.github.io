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

- [*Archive*](archive.md)
