---
title: "Twig-join-merge-and-other-fun-stuff"
layout: post
---
Not much logic should be created in a view.

That being said,some parts of logic, despite being simple, end up being quite big, but it doesn't make _much sense_ have it in an external controller.

```
{% if tags is defined %}
    {% for tag in tags %}
        {% set active = false %}
        {% if tag in selectedTags %}
            {# If the tag is already selected, we remove it #}
            {% set tagsToSend = [] %}
            {% for selectedTag in selectedTags %}
                {% if tag != selectedTag %}
                    {% set tagsToSend = tagsToSend|merge([selectedTag]) %}
                {% else %}
                    {% set active = true %}
                {% endif %}
            {% endfor %}
        {% else %}
            {# If the tag is not selected, we add it to the URL #}
            {% set tagsToSend = selectedTags | merge([tag]) %}
        {% endif %}
        {% if tagsToSend|length >= 1 %}
            <a id="button_timelapse_{{ tag }}" type="button" class="btn btn-default {% if active == true %}active{% endif %}" href="{{ path('SPIntelligenceBundle_dashboard_with_tags', { 'slug':'product-dashboard-dc-ios', 'tags': tagsToSend|join('+')  }) }}">{{ tag }}</a>
        {% else %}
            <a id="button_timelapse_{{ tag }}" type="button" class="btn btn-default active" href="{{ path('SPIntelligenceBundle_dashboard', { 'slug':'product-dashboard-dc-ios' }) }}">{{ tag }}</a>
        {% endif %}
    {% endfor %}
{% endif %}
```
