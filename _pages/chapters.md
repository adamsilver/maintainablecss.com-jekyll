---
layout: chapters
id: chapters
permalink: /chapters/
title: "Chapters"
---

{% assign prefaceChapters = site.chapters | where:'section', 'Preface' %}
{% assign backgroundChapters = site.chapters | where:'section', 'Background' %}
{% assign coreChapters = site.chapters | where:'section', 'Core' %}
{% assign extraChapters = site.chapters | where:'section', 'Extras' %}

# Chapters

## Preface

<ol>
  {% for chapter in prefaceChapters %}
    <li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
  {% endfor %}
</ol>

## Background

{% assign backgroundStart = prefaceChapters.size | plus: 1 %}

<ol start="{{backgroundStart}}">
  {% for chapter in backgroundChapters %}
    <li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
  {% endfor %}
</ol>

## Core

{% assign coreStart = backgroundStart | plus: backgroundChapters.size %}

<ol start="{{coreStart}}">
	{% for chapter in coreChapters %}
		<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
	{% endfor %}
</ol>

## Extras

{% assign extrasStart = coreStart | plus: coreChapters.size %}

<ol start="{{extrasStart}}">
	{% for chapter in extraChapters %}
		<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
	{% endfor %}
</ol>