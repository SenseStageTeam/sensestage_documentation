---
layout: page
---

To add something in the automated lists use one of these possible options for status in the front matter:

```
status: complete
status: fixmesoon
status: backlist
```

The unsorted list is generated from those pages that have 'todo' in their tags.


# guides that we need that aren't there yet

*manual list of what we need guides on*

- a nice guide on getting accelerometer data

# pages that really should be fixed soon

{% for coll in site.collections %}

{% if coll.docs.size > 0 %}
<ul>
{% assign thesepages = coll.docs | where: "status", "fixmesoon" %}
{% if thesepages.size > 0 %}
    {% for post in thesepages %}
<li><a href="{{post.url}}">{{ post.title }}</a></li>
    {% endfor %}
{% endif %}
</ul>    
{% endif %}
{% endfor %}

# backlist

{% for coll in site.collections %}

{% if coll.docs.size > 0 %}
<ul>
{% assign thesepages = coll.docs | where: "status", "backlist" %}
{% if thesepages.size > 0 %}
    {% for post in thesepages %}
<li><a href="{{post.url}}">{{ post.title }}</a></li>
    {% endfor %}
{% endif %}
</ul>    
{% endif %}
{% endfor %}

# unsorted

{% for coll in site.collections %}

{% if coll.docs.size > 0 %}
<ul>
{% assign thesepages = coll.docs %}
{% if thesepages.size > 0 %}
    {% for post in thesepages %}
    {% if post.tags contains 'todo' %}
<li><a href="{{post.url}}">{{ post.title }}</a></li>
    {% endif %}
    {% endfor %}
{% endif %}
</ul>    
{% endif %}
{% endfor %}

# complete

{% for coll in site.collections %}

{% if coll.docs.size > 0 %}
<ul>
{% assign thesepages = coll.docs | where: "status", "complete" %}
{% if thesepages.size > 0 %}
    {% for post in thesepages %}
<li><a href="{{post.url}}">{{ post.title }}</a></li>
    {% endfor %}
{% endif %}
</ul>    
{% endif %}
{% endfor %}

# Assume to be complete

*without todo tag or status in front matter*

{% for coll in site.collections %}

{% if coll.docs.size > 0 %}
<ul>
{% assign thesepages = coll.docs %}
{% if thesepages.size > 0 %}
    {% for post in thesepages %}
    {% unless post.tags contains 'todo' %}    
        {% unless post.status %}
            <li><a href="{{post.url}}">{{ post.title }}</a></li>
        {% endunless %}
    {% endunless %}
    {% endfor %}
{% endif %}
</ul>    
{% endif %}
{% endfor %}
