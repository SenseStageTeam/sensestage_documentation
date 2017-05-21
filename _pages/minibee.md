---
layout: page
---



# Getting started

Here are a few links to get started right away. Below you find a full overview of the documentation. If you have any questions, please join us on the [Sense/Stage Forum](https://forum.sensestage.eu).

* [An overview of the Sense/Stage MiniBee system](../minibee/overview-of-the-system)
* [Unpacking the Sense/Stage MiniBee kit](../minibee/getting-started-with-sense-stage)

<hr>

*This page is currently a work in progress. See [here](https://docs.sensestage.eu/old/topic/documentation) for an overview of the old documentation. In the pages below the old sites are linked where necessary.*

*If you want to help out in the documentation process, please read on [how to contribute](general/contributing-to-the-documentation).*

{% assign coll = site.collections.minibee %}
{{ coll.docs.size }}

<hr>

{% if coll.output %}
{% if coll.docs.size > 0 %}
<hr>
# {{ coll.label | capitalize }} documentation {#sensestage{{ coll.label }}}
{% include allcollection_index.html collname = coll.label %}
  {% for cat in site.data.category_order.navigation %}
    {% if cat.children != null %}
        {% assign hasNoPages = true %}
        {% for child in cat.children %}
        {% assign thesepages = coll.docs | where: "category", cat.name | where: "subcategory", child.name %}
            {% if thesepages.size > 0 %}
<hr>
                {% if hasNoPages %}
## {{ cat.name | capitalize }} {#{{cat.name}}}
                {% endif %}
                {% assign hasNoPages = false %}
                {% assign hasOverview = 0 %}
                {% for post in thesepages %}
                    {% if post.type == "overview" %}
### <a href="{{post.url}}">{{ post.title }}</a> {#{{child.name}}}
{% if post.summary %}*{{ post.summary }}*{% endif %}
                    {% assign hasOverview = 1 %}
                    {% endif %}
                {% endfor %}
                {% if hasOverview == 0 %}
### {{ child.name | capitalize }} {#{{child.name}}}
                {% endif %}
{% include category_index.html collname = coll.label catname=cat.name subcatname=child.name %}
                {% for post in thesepages %}
                    {% unless post.type == "overview" %}
* <a href="{{post.url}}">{{ post.title }}</a> {% if post.summary %}: {{ post.summary }}  {% endif %}
                    {% endunless %}
                {% endfor %}

            {% endif %}
        
        {% endfor %}
    {% else %}
<hr>
        {% assign thesepages = coll.docs | where: "category", cat.name %}
        {% assign hasOverview = 0 %}
        {% if thesepages.size > 0 %}
            {% for post in thesepages %}
                {% if post.type == "overview" %}
## <a href="{{post.url}}">{{ post.title }}</a> {#{{cat.name}}}
{% if post.summary %}*{{ post.summary }}*{% endif %}
                    {% assign hasOverview = 1 %}
                {% endif %}
            {% endfor %}

            {% if hasOverview == 0 %}
## {{ cat.name | capitalize }} {#{{cat.name}}}
            {% endif %}
                
            {% for post in thesepages %}
                {% unless post.type == "overview" %}
* <a href="{{post.url}}">{{ post.title }}</a> {% if post.summary %}: {{ post.summary }}  {% endif %}
                {% endunless %}
            {% endfor %}
        {% endif %}
     {% endif %}
  {% endfor %}
{% endif %}
{% endif %}
