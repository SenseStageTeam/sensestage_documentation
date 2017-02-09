---
layout: page
---

## MiniBee Documentation

{% assign minibeegroups = site.minibee | group_by: "category" | sort: "name" %}

{% for group in minibeegroups %}
# {{ group.name | capitalize }}

{% for post in site.minibee %}
{% if post.category == group.name %}
* <a href="{{post.url}}">{{ post.title }}</a> {% if post.summary %}: {{ post.summary }}  {% endif %}
{%endif%}
{%endfor%}

{%endfor%}
