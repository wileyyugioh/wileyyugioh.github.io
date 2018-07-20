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
    {% capture cache %}
        {% assign temp_d = post.date | date: "%-d" %} 
        {% assign temp_m = post.date | date: "%B" %} 
        {% case temp_m %}
            {% when 'April' or 'May' or 'June' or 'July' %}{% assign m = temp_m %}
            {% when 'September' %}{% assign m = 'Sept.' %}
            {% else %}{% assign m = post.date | date: "%b." %}
        {% endcase %}
        {% case temp_d %}
            {% when '1' or '21' or '31' %}{% assign d = temp_d | append: 'st' %}
            {% when '2' or '22' %}{% assign d = temp_d | append: 'nd' %}
            {% when '3' or '23' %}{% assign d = temp_d | append: 'rd' %}
            {% else %}{% assign d = temp_d | append: 'th' %}
        {% endcase %}
    {% endcapture %}{% assign cache = nil %}
    {{ m }} {{ d }}, {{ post.date | date: "%Y" }}: <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
    <li><a href="/archive"><strong>Archive</strong></a></li>
</ul>
