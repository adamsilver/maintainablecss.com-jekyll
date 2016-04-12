---
layout: chapters
id: chapters
permalink: /chapters/
title: "Chapters"
---

# Chapters

## Preface

<ol>
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Preface' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>

## Background

<ol start="2">
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Background' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>

## Core

<ol start="5">
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Core' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>

## Extras

<ol start="8">
	{% for chapter in site.chapters %}
		{% if chapter.section == 'Extras' %}
			<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
		{% endif %}
	{% endfor %}
</ol>