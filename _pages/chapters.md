---
layout: chapters
id: chapters
permalink: /chapters/
title: "Chapters"
---

# Chapters

<ol>
	{% for chapter in site.chapters %}
		<li>
			<a href="{{ chapter.url }}"> {{ chapter.title }} </a>
		</li>
	{% endfor %}
</ol>