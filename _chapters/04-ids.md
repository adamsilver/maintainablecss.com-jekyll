---
layout: chapter
title: ID attributes
section: Background
permalink: /chapters/ids/
---

In short: **Don't** use IDs as hooks for styling. Only use class names. You may use IDs for other things as we will see shortly.

## Why? Because of specificity

[IDs over power class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude. For this reason you can't override an ID selector's style with a class name selector easily.

And of course you can't have multiple IDs but you can have multiple class names. Useful for state as we will see in a later chapter.

## But I need to use an ID?

ID's are useful and *necessary* for many aspects of web development, but CSS is not one of those. Here are two examples, both of which **improve the user experience**.

1. **Form controls** are linked to labels via `id` and `for` attributes.
2. **Internal anchors** work off of ID attributes.

Note: when you do use an ID, use the same conventions as described for classes. This helps keep components modular.