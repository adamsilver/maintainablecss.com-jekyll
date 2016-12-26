---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

If you can't find an answer, please [raise an issue on Github](https://github.com/adamsilver/maintainablecss.com/issues/new). Thanks!

## When should I use this?

This approach works well when your building long-lived, bespokely designed, responsive sites that scale and evolve over time.

## What if I don't want to use it?

If you don't like it, feel free not to use it. Or use the bits you do like. If something isn't working well, please let me know and perhaps we can document how to solve this for everyone else.

## Isn't this the same as [insert methodology here]?

These guides are the result of building many different types of websites. I've been influenced by many different experiences, requirements and people that I've worked with.

No doubt, there is a resemblance to BEM and ECSS. If you're using those happily, stick with them. These guides are here if and when you need them.

## Can I translate your book?

Yes. Please contact me to find out more. Here's the [Japanese version](http://coliss.com/articles/build-websites/operation/css/maintainable-css-by-adam.html).

## Must I give a class name to every element?

The short answer is no. You can write `.module h2` if you want to and sometimes you may have to. Perhaps you're using Markdown.

## Why must I prefix components with the module name?

Good question. I used to write components without the prefix too but ran into problems. I used to do this:

	<div class="basket">
	    <div class="heading">

And this:

	/* module */
	.basket {}

	/* heading component of basket module */
	.basket .heading {}

There are two problems:

1. When viewing HTML, you can't easily differentiate between a module and a component.
2. The `.basket .heading` component will inherit styles from the `.heading` module. 

## What about common styles e.g. buttons?

Depending on your visual design requirements buttons can be problematic. They often have different spacing, floating, and other display rules depending on their location. There is also Media Queries to consider.

For example, in one module a button might be floated right within a container that has some text to the left of it. In another module it might be centered with a fixed width and some small text beneath with `margin-bottom` for spacing.

It becomes really tricky trying to abstract the common rules because you don't want to end up in a situation where you have to override. Or worse that you're worried to update the abstracted set of CSS rules.

However, if you do decide that abstraction is useful there are two approaches you can take.

The first is to comma delimit several different buttons to apply the same styles as follows:

	.basket-removeButton,
	.another-loginButton,
	.another-deleteButton {
      /*common styles*/
	}

The second approach is to make a button into a module:

	.primaryButton {
	  /*common styles*/
	}

On a recent project I went for something in between. I was building a checkout flow. On each page there was a "continue" button that was identical on each page. There was also a "back" link. I ended up with this:

	.checkoutActions-continueButton {
	  /*...*/
	}

	.checkoutActions-backButton {
	  /*...*/
	}

This approach meant that I segmented the abstraction to known identical modules, improving maintainability without affecting other similar (but not identical) buttons.

## What about inheritance for things like `h1`s etc?

If your `h1`s are (almost always) identical on every page and every module then feel free to specify styles like this:

	h1 {
      font-size: ...;
	  color: ...;
	}

However, in my experience, this is *rarely* the case, and so I wouldn't advise this&mdash;instead keep styles encapsulated to the module like this:

	/* <h1 class="module-heading"> */
	.module-heading {
	  font-size: ...;
	  color: ...;
	}

## Where do I put Media Queries?

Generally speaking, the screen should adapt to the content, not the other way around. This means that a module's breakpoints are determined by the module itself, and *not* by a predetermined set of breakpoints such as "small", "medium" and "large". Doing it this way would constrain the design and quite possibly degrade the User Experience unnecessarily.

Therefore, all styles&mdash;even those that are wrapped in Media Queries&mdash;should be located next to regular styles:

	.basket {}

	@media(min-width: 500px) {
        .basket {}
	}

	@media(min-width: 1000px) {
	    .basket {}
	}

	.basket-heading {}

## Where do I put modifiers and states?

Just like media queries, states and modifiers should be located in close proximity to the element they pertain to:

	.basket {}

	.basket-isHidden {}

	.basket-heading {}

	.basket-heading-someModifier {}

## Should I add comments?

If you take an approach whereby multiple modules reside within a single CSS file, it's a good idea to segregate those with a chunky comment:

	/********************************************
	* Basket
	********************************************/

	.basket {}

	.basket-heading {}

	/********************************************
	* Thinger
	********************************************/

	.thinger {}

	.thinger-details {}

## Can't find an answer here?

Raise an issue on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you as soon as I can. Thanks!
