---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

If you can't find an answer, please [raise an issue on Github](https://github.com/adamsilver/maintainablecss.com/issues/new). Thanks!

## Can I translate this?

Yes. To do this:

1. [Fork the repo](https://github.com/adamsilver/maintainablecss.com/).
2. Point your (country code) domain to it.
3. Cite the original and let me know :).

## What about inheritance for headings etc?

Ideally our semantic HTML matches the integrity of the visual design. Meaning that we would hope that all `h1`s are identical. In this case we can declare the following CSS:

	h1 {
      /* etc */
	}

However, this is rarely the case, in commercial, large-scale websites. In this case we should encapsulate styles to the module in question:

	.module-heading {
	  font-size: ...;
	  color: ...;
	}

<!--## Where do I put media queries?

The screen should adapt to the content, not the other way around.

This means a module's breakpoints shouldn't be predetermined by *small*, *medium* and *large*. Doing this constrains the design and degrades the user experience.

Therefore, all styles&mdash;even those that are wrapped in media queries&mdash;should be located next to regular styles:

	.basket {}

	@media(min-width: 500px) {
      .basket {}
	}

	@media(min-width: 1000px) {
	  .basket {}
	}

	.basket-heading {}

## Where do I put modifiers and states?

States and modifiers, similarly to media queries, should be located in close proximity to the element they pertain to:

	.basket {}

	.basket-isHidden {}

	.basket-heading {}

	.basket-heading--someModifier {}-->

## Can't find an answer here?

Raise an issue on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you as soon as I can. Thanks!
