---
layout: chapter
title: IDs
permalink: /chapters/5/
---

IDs are problematic because of their super powers with regards to [specificity](http://www.w3.org/TR/css3-selectors/#specificity).

But sometimes we need IDs in our HTML&mdash;form controls are linked to labels via `id` and `for` attributes. Sometimes we need to utilise internal anchors to allow the user to scroll to various parts of the page. Both of these examples improve the user experience.

So the short of it is that an ID should be used for additional behaviour like I just mentioned but they shouldn't be used for CSS.

When you do use an ID, use the same convention as the CSS.