---
layout: default
id: home
---

# Maintainable CSS

**Warning:** this is a work in progress. Read stuff and it will be a bit of a waste of time at this stage. I am designing and developing to live. #sorrynotsorry

## Chapters

<ol>
	{% for chapter in site.chapters %}
		<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
	{% endfor %}
</ol>