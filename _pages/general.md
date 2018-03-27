---
layout: page
permalink: /general/
---

{% assign collname = "general" %}


{% for coll in site.collections %}
{% if site.data.category_order.toplevelcategories contains coll.label %}
{% if coll.label == collname %}
{% if coll.docs.size > 0 %}
<hr>
<!-- # {{ coll.label | capitalize }} documentation {#sensestage{{ coll.label }}} -->
  {% for cat in site.data.category_order.navigation %}
    {% if cat.children != null %}
        {% assign hasNoPages = true %}
        {% for child in cat.children %}
        {% assign thesepages = coll.docs | where: "category", cat.name | where: "subcategory", child.name %}
            {% if thesepages.size > 0 %}
{% include collection_index.html collname = coll.label catname=cat.name %}
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
