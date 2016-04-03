---
layout: default
id: home
---

# MaintainableCSS

*MaintainableCSS* is an approach to writing CSS that is modular, and easy to maintain. Find out more by running through each short chapter.

## Chapters

I have grouped the chapters in to various sections. If you want the *how* without the *why* then you can jump to the Core section.

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