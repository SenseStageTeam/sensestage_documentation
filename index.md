---
layout: page
---

# MiniBee Documentation

  {% for cat in site.data.category_order.navigation %}
    {% if cat.children != null %}
## {{ cat.name | capitalize }}
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
### {{ child.name | capitalize }}
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
