---
layout: page
---

## MiniBee Documentation

{% assign cats = site.minibee | group_by: "category" | sort: "name" %}

{% assign subcats = site.minibee | group_by: "subcategory" | sort: "name" %}

{% for group in cats %}

# {{ group.name | capitalize }}

        {% for subgroup in subcats %}

        {% assign thesepages = site.minibee | where: "category", group.name | where: "subcategory", subgroup.name %}

            {% if thesepages.size > 0 %}

                {% assign hasOverview = 0 %}
                {% for post in thesepages %}
                    {% if post.type == "overview" %}
## <a href="{{post.url}}">{{ post.title }}</a>
{% if post.summary %}*{{ post.summary }}*{% endif %}
                    {% assign hasOverview = 1 %}
                    {% endif %}
                {% endfor %}
                {% if hasOverview == 0 %}
## {{ subgroup.name | capitalize }}
                {% endif %}

                {% for post in thesepages %}
                    {% unless post.type == "overview" %}
* <a href="{{post.url}}">{{ post.title }}</a> {% if post.summary %}: {{ post.summary }}  {% endif %}
                    {% endunless %}
                {%endfor%}

            {% endif %}

        {%endfor%}

{%endfor%}
