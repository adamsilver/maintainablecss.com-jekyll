---
layout: default
id: home
---

# MaintainableCSS

*MaintainableCSS* is an approach to writing CSS that is modular, and easy to maintain. Find out more by running through each short chapter.

## Benefits of Maintainable CSS

1. **Modular and encapsulated** styles that don't bleed or cascade without *your* permission.
2. **Any design, any website** &mdash; completely flexible to *your* requirements.
3. **Requires no tooling** &mdash; feel free to use tooling, but there is no requirement
4. **There is very little to learn** &mdash; read the guides and see.
5. **Small or big** &mdash; works for any size project.
6. **Retrospective addition** &mdash; use it in your current project and start to feel the benefits bit by bit.
7. **No problem of specificity** &mdash; learn to avoid problems of specificity and require no overrides. Like every piece of CSS you write is a blank canvas.
8. **Managing state is easy** &mdash; change look and feel based on state with ease.
9. **No worry of regression** &mdash; when you change existing styles.
10. **Any team size** &mdash; helpful in a team of one, vital in a team of more.
11. **Semantic HTML and CSS** &mdash; easy to understand code, even if your new to the codebase.
12. **High performance** &mdash; flat and performant selectors.

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