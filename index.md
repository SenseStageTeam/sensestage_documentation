---
layout: page
---

This page is currently a work in progress. See [here](https://docs.sensestage.eu/old/topic/documentation) for an overview of the old documentation. In the pages below the old sites are linked where necessary. If you want to help out in the documentation process, please read on [how to contribute](minibee/contributing-to-sense-stage).

# MiniBee Documentation {#sensestageminibee}

  {% for cat in site.data.category_order.navigation %}
    {% if cat.children != null %}
## {{ cat.name | capitalize }} {#{{cat.name}}}
        {% for child in cat.children %}
        {% assign thesepages = site.minibee | where: "category", cat.name | where: "subcategory", child.name %}
            {% if thesepages.size > 0 %}
                {% assign hasOverview = 0 %}
                {% for post in thesepages %}
                    {% if post.type == "overview" %}
### <a href="{{post.url}}">{{ post.title }}</a>
{% if post.summary %}*{{ post.summary }}*{% endif %}
                    {% assign hasOverview = 1 %}
                    {% endif %}
                {% endfor %}
                {% if hasOverview == 0 %}
### {{ child.name | capitalize }} {#{{child.name}}}
                {% endif %}

                {% for post in thesepages %}
                    {% unless post.type == "overview" %}
* <a href="{{post.url}}">{{ post.title }}</a> {% if post.summary %}: {{ post.summary }}  {% endif %}
                    {% endunless %}
                {%endfor%}

            {% endif %}
        
        {% endfor %}
    {% endif %}
  {% endfor %}
