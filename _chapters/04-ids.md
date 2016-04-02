---
layout: chapter
title: Don't use IDs
section: Background
---

IDs are problematic because of their super powers with regards to [specificity](http://www.w3.org/TR/css3-selectors/#specificity) so avoid them as hooks for styling.

Specificity becomes a problem when you *want* to override a module's style. One reason for that might be due to *state*, something which is discussed in a later chapter.

For now you just need to know that:

1. you can't have multiple ids on a single element.
2. whilst you can have an id *and* a class attribute, the id will override the class, because of specificity.

So in summary, just use classes, as they have the same power of specificity. This means any properties in second class will override the first, as intended.

## But, sometimes we need IDs?

It's important to note, that ID's are useful and *necessary* for many aspects of web development, but CSS is not one of those. Here are two examples, both of which **improve the user experience**.

1. **Form controls** are linked to labels via `id` and `for` attributes.
2. **Internal anchors** work off of ID attributes.

Note: when you do use an ID, use the same conventions as described for classes. This helps keep components modular.