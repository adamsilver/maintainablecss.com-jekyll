---
layout: chapter
title: 5. A note about IDs
id: chapter5
permalink: /chapters/5/
previousPage:
  href: /chapters/4/
nextPage:
  href: /chapters/6/
---

Sometimes we need IDs in our HTML. Form controls are linked to labels via `id` and `for` attributes. Sometimes we need to utilise internal anchors to allow the user to scroll to various parts of the page. Both of these examples improve the user experience.

With that said it is well known that IDs have super powers when it comes to [specificity](http://www.w3.org/TR/css3-selectors/#specificity).

So in short, use IDs as a bonus to provide bonus behaviour. But in terms of making it easy to work with CSS, use classes.