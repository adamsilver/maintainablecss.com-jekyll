---
layout: default
id: home
---

# Maintainable CSS

**Warning:** this is a complete work in progress. Read stuff and it will be a bit of a waste of time at this stage. I am designing and developing to live. #sorrynotsorry

## Chapters

<ul>
	{% for p in site.pages %}
		{% if p.layout == "chapter" %}
			<li>
	  			<a href="{{ p.url }}">{{ p.title }}</a>
			</li>
		{% endif %}
	{% endfor %}
</ul>