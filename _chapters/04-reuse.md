---
layout: chapter
title: Reuse
permalink: /chapters/4/
---

Typically, reuse is important when it comes to software engineering and I strive for it every day.

However, I won't blindly abstract something unless it's useful to do so. And when it comes to CSS, I take a duplication first approach for various important reasons.

Let's take a look at a couple of interesting examples

## e.g. Clearfix

	.clearfix {}

## e.g. Red

	.red {}

The interesting thing about each of these class names is how they are nothing to do with what the element is, but to do with how the element *looks*. This breaks [semantics](/chapters/2/) which in turn break foundations which cause all sorts of problems.