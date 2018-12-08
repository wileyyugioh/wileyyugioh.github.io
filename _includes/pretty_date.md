{% capture cache %}
    {% assign in_date = include.date %}
    {% assign temp_d = in_date | date: "%-d" %} 
    {% assign temp_m = in_date | date: "%B" %} 
    {% case temp_m %}
        {% when 'April' or 'May' or 'June' or 'July' %}{% assign m = temp_m %}
        {% when 'September' %}{% assign m = 'Sept.' %}
        {% else %}{% assign m = in_date | date: "%b." %}
    {% endcase %}
    {% case temp_d %}
        {% when '1' or '21' or '31' %}{% assign d = temp_d | append: 'st' %}
        {% when '2' or '22' %}{% assign d = temp_d | append: 'nd' %}
        {% when '3' or '23' %}{% assign d = temp_d | append: 'rd' %}
        {% else %}{% assign d = temp_d | append: 'th' %}
    {% endcase %}
{% endcapture %}{% assign cache = nil %}
{{ m }} {{ d }}, {{ in_date | date: "%Y" }}