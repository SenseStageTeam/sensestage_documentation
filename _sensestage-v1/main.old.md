---
layout: documentation
title: Sense/Stage Documentation
summary: Sense/Stage v1 Documentation Pages
permalink: /sensestage-v1-old/
creation-date: 2017-02-06
---

One this page you will find a full list of all the available documentation pages for Sense/Stage v1. Note that some of these pages are stubs, and therefore may not yet be finished. If you have any questions, please join us on the [Sense/Stage Forum](https://forum.sensestage.eu). And if you would like to help contribute to the documentation process, please read on [how to contribute](general/contributing-to-the-documentation).*

<hr>

# Getting started

To get started right away, you should first read through [an overview of the Sense/Stage system](overview-of-the-system). Once you're familiar with that, proceed on to the [Getting Started Guide for New Users](getting-started-with-sense-stage/getting-started-with-sense-stage).  

You will find additional guides, technical reference pages, and download links using the navigation links in the header above.

<hr>

{% assign collname = "sensestage-v1" %}


{% for coll in site.collections %}
{% if site.data.category_order.toplevelcategories contains coll.label %}

{% if coll.label == collname %}

{% if coll.docs.size > 0 %}

<hr>
<!-- # {{ coll.label | capitalize }} documentation {#sensestage{{ coll.label }}} -->
<!-- {% include allcollection_index.html collname = coll.label %} -->
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
<!-- {% include category_index.html collname = coll.label catname=cat.name subcatname=child.name %} -->
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
{% endif %}
{% endfor %}
