---
layout: chapter
title: Don't use IDs
---

IDs are problematic because of their super powers with regards to [specificity](http://www.w3.org/TR/css3-selectors/#specificity) so don't use them in CSS.

In the chapter about semantics I mentioned that you don't really need more than one class name per element when you name things semantically. I lied, sorry! I will show in later chapters how this might be necessary.

Just know that you can't have multiple IDs, and that this means that if you do use an ID for styling, that overriding that style becomes painful due to the aformentioned specificity.

**Just don't bother.**

## IDs are not all bad

Form controls are linked to labels via `id` and `for` attributes. Internal anchors work off of ID attributes. Both of these examples improve the user experience.

When you do use an ID, use the same conventions as described for classes. This helps keep components modular.