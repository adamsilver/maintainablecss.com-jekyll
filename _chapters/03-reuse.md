---
layout: chapter
title: Reuse
permalink: /chapters/3/
---

Much like Semantics, there is a good reason why the topic of Reuse is placed so early on in *Maintainable CSS* &mdash; that's because the principles of DRY are valid and ever present throughout software engineering practices.

However, I think it's fair to say that when it comes to CSS, striving for reuse is something that causes CSS to become problematic in terms of maintainability &mdash; which is strange because the principles of DRY are there to aid maintainability.

I take a duplication-first approach to development anyway. Duplication is the simplest strategy. Don't get me wrong duplication is not advised without thought. It's just that the process of duplication allows you as a developer to feel the pain first, then realise that abstraction (for reuse) is worth your time and will add value.

But, when it comes to CSS, reuse can be very problematic and this has been discussed briefly in the chapter on Semantics. However, let's take a slightly different look:

1. Clearfix
2. Red

The interesting thing about each of these class names is how they are nothing to do with what the element is, but to do with how the element *looks*. This breaks [semantics](/chapters/2/) which in turn break foundations which cause all sorts of problems.

(Flesh out)