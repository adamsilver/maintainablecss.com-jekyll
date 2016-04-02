---
layout: default
id: home
---

# Maintainable CSS

*Maintainable CSS* is an approach to writing CSS that is easy to maintain and scales well. Find out more by running through each short chapter.

## Chapters

### Preface

<ol>
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Preface' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>

### Background

<ol start="2">
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Background' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>

### Core

<ol start="5">
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Core' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>

## Got a question, issue or suggestion?

Just [raise an issue for discussion](http://github.com/adamsilver/maintainablecss.com/issues/new/) on Github.