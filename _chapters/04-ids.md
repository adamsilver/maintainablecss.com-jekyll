---
layout: chapter
title: Don't use IDs
---

IDs are problematic because of their super powers with regards to [specificity](http://www.w3.org/TR/css3-selectors/#specificity) so avoid them as hooks for styling.

Specificity becomes a problem when you *want* to override a module's styles based on *state*, something that is discussed in later chapters.

All you need to know now is the following:

## 1. You can't have multiple IDs because it's invalid:

This is invalid:

	<div id="someModule someModule-someState">
	</div>

## 2. You can do this but it has specificity issues:

That is, the state class needs to override the id. But the id is more powerful than the class:

	<div id="someModule" class="someModule-someState">
	</div>

## 3. You can do this and it works as intended:

The second css class will override the defaults as intended:

	<div class="someModule someModule-someState">
	</div>

In the chapter about semantics, I mentioned that you don't really need more than one class name per element when you name things semantically&mdash;sorry to say I lied.

Multiple class names are needed for state, something we discuss in a later chapter.

## Sometimes we must use IDs

It's important to note, that ID's are useful and *necessary* for many aspects of web development, but CSS is not one of those. Here are two examples, both of which **improve the user experience**.

1. **Form controls** are linked to labels via `id` and `for` attributes.
2. **Internal anchors** work off of ID attributes.

Note: when you do use an ID, use the same conventions as described for classes. This helps keep components modular.