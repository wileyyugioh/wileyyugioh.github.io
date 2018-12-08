---
title: Home
---

### Stuff I've done

- [birddb - a crowd-sourced database of birds (may be down if I run out of hosting credit)](https://github.com/wileyyugioh/birddb)

- [NylonSock - a C++ networking library in the style of socket.io](https://github.com/wileyyugioh/NylonSock)

- [Osu-Touchpad - a tablet emulator for mobile devices using Node.js](https://github.com/wileyyugioh/Osu-Touchpad)

### Writeups I think are neat

<ul>
    {% for post in site.posts limit:5 %}
    <li>
        {% include pretty_date.md date=post.date %}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
    <li><a href="/archive"><strong>Archive</strong></a></li>
</ul>
