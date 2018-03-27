---
layout: page
permalink: /sensestage-v1/
---



# Getting started

Here are a few links to get started right away. Below you find a full overview of the documentation. If you have any questions, please join us on the [Sense/Stage Forum](https://forum.sensestage.eu).

* [An overview of the Sense/Stage MiniBee system](../minibee/overview-of-the-system)
* [Unpacking the Sense/Stage MiniBee kit](../minibee/getting-started-with-sense-stage)

<hr>

*If you want to help out in the documentation process, please read on [how to contribute](general/contributing-to-the-documentation).*


{% assign collname = "sensestage-v1" %}


{% for coll in site.collections %}
{% if site.data.category_order.toplevelcategories contains coll.label %}
{% if coll.label == collname %}
{% if coll.docs.size > 0 %}
<hr>
# {{ coll.label | capitalize }} documentation {#sensestage{{ coll.label }}}
  {% for cat in site.data.category_order.navigation %}
    {% if cat.children != null %}
        {% assign hasNoPages = true %}
        {% for child in cat.children %}
        {% assign thesepages = coll.docs | where: "category", cat.name | where: "subcategory", child.name %}
            {% if thesepages.size > 0 %}
<hr>
                {% if hasNoPages %}
## {{ cat.name | capitalize }} {#{{cat.name}}}
{% include collection_index.html collname = coll.label catname=cat.name %}
                {% endif %}
                {% assign hasNoPages = false %}
                {% assign hasOverview = 0 %}
1, {{ cat.name }}, {{ child.name }}                
                {% for post in thesepages %}
{{ cat.name }}, {{ child.name }}                
{{ post.title }}, {{ post.type }}
                    {% if post.type == "overview" %}
### <a href="{{post.url}}">{{ post.title }}</a> {#{{child.name}}}
{% if post.summary %}*{{ post.summary }}*{% endif %}
                    {% assign hasOverview = 1 %}
                    {% endif %}
                {% endfor %}
                {% if hasOverview == 0 %}
### {{ child.name | capitalize }} {#{{child.name}}}
                {% endif %}
2, {{ cat.name }}, {{ child.name }}, {{ thesepages }}             
                {% for post in thesepages %}
3, {{ cat.name }}, {{ child.name }}                         
{{ post.title }}, {{ post.type }}
                    {% unless post.type == "overview" %}
* <a href="{{post.url}}">{{ post.title }}</a> {% if post.summary %}: {{ post.summary }}  {% endif %}
                    {% endunless %}
                {% endfor %}

            {% endif %}
        
        {% endfor %}
     {% endif %}
  {% endfor %}
{% endif %}
{% endif %}
{% endif %}
{% endfor %}
