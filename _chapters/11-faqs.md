---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

Can't find your answer here? Raise an issue on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you as soon as I can. Thanks!

## When should I use this?

MaintainableCSS is an approach that works well when building long-lived, bespokely designed responsive websites that you want to scale. It's also useful for websites that evolve over time.

## What if I don't want to use it?

If you don't like it, feel free not to use it, or take the bits and pieces that you do like&mdash;please tell me though what didn't work and why, as i'd love to know more so that we can learn together.

## Isn't this the same as [insert methodology here]?

These guides are the result of building many different types of websites and have been influenced by many experiences and the many people I have worked with.

With that said, I think it bares most resemblance to BEM and ECSS, so if you're using those or any other methodology that works for you, stick with it. These guides will be here if and when required.

## Can I translate your book?

It's already been translated to [Japanese](http://coliss.com/articles/build-websites/operation/css/maintainable-css-by-adam.html) and German and Spanish are both on the way. So yes, please get in touch to find out how to do this.

## Must I give a class name to every element?

The short answer is no.

Most of the time it is better to provide and target elements via a class as it makes your code consistent, easy to reason about, performant and portable. But if you decide to do this: `.module h2` it's not going to be the end of the world.

Also you may have to do something like that because you might be using Markdown (or a similar constraint) in which case you will *need* to target elements rather than class names as follows:

	.someModule h1 {}
	.someModule h2 {}
	.someModule p {}
	.someModule ul {}

## Why must I prefix components with the module name?

Good question. I actually used to write components without the prefix too but ran into problems...

The HTML I used to write looked something like this:

	<div class="basket">
	    <div class="heading">

And the CSS looked something like this:

	/* module */
	.basket {}

	/* heading component of basket module */
	.basket .heading {}

The first problem is that when viewing the HTML, you can't easily differentiate between a module and a component, which makes maintainence a bit harder.

The second problem is that the `.basket .heading` *component* will incorrectly inherit the styles from the `.heading` *module* which is something we don't want, we want our styles encapsulated and bound to the module.

Similarly, I recently built a shop where there was a *Delivery &amp; Returns* module and a Delivery &amp; Returns *page* with the following CSS causing problems:

	/* module */
	.productDetails .deliveryAndReturns {}

	/* page */
	.deliveryAndReturns {}

The page styles intefered with the module styles.

## What about common styles used in many places e.g. buttons?

Depending on your visual design requirements buttons can be problematic because they often have different spacing, floating, and other display rules depending on their location, not to mention media queries.

As a very *simple* example: in one module a primary button might be floated right within a container that has some text to the left of it. And in another module it might be centered with a fixed width and some small text beneath with `margin-bottom` for spacing.

It becomes really tricky trying to abstract the common rules because you don't want to end up in a situation where you have to override, or worse that you're worried to update the abstracted set of CSS rules.

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

On a recent project I actually went for something in between. I was building a checkout flow. On each page there was a "continue to next step" button that was identical on each of the pages. There was also a "back to previous step" link so I ended up with this:

	.checkoutActions-continueButton {
	  /*...*/
	}

	.checkoutActions-backButton {
	  /*...*/
	}

This approach meant that I segmented the abstraction to known identical modules, improving maintainability without affecting other similar (but not identical) buttons.

## What about inheritance for things like h1's etc?

If yor `h1`s are (almost always) identical on every page and every module then feel free to specify styles like this:

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




