---
layout: chapter
title: Modules
section: Core
permalink: /chapters/modules/
---

## What's a module?

A module is a distinct, independent unit, that can be combined with other modules to form a more complex structure.

In a living room, you can consider the TV, the sofa and the wall art modules. All coming together to create a useable room.

If you take one of the units away, the rest still works just fine. I don't need the TV to be able to sit on the sofa etc.

**In a website each of these can be considered modules:** header, footer, search form, sign up form, shopping basket, article, product list, navigation, homepage promo, archive list etc.

## What's a component?

A module is made up of components. Without the components, the module is incomplete or broken.

For example a sofa is made up of the frame, upholstry, legs, cushions and back pillows. These are all required components to make the sofa function as designed.

A logo *module* might consist of copy, an image and a link: each of which are components. Without the image, the logo is broken, without the link, the logo is incomplete.

## Modules vs components

Sometimes it can be tricky to decide whether something is a component or a module. For example a header is a module and it might contain a logo and a navigation menu as part of it. Are these components or modules?

Ultimately it doesn't matter too much and you can use your own experience to decide. For me, in a recent project it made sense for the logo to be a component of the header, and the navigation menu to be a module within the header.

Regardless, *MaintainableCSS* doesn't force anything because it cannot understand *your* project requirements like you do. This point is addressed because sometimes we can get hung up on these things, but most of the time it is very clear what is what.

And afterall, it's extremely is to switch HTML class names from the component convention to the module convention and vice versa.

## Creating a module

Let's build a module together. We're going to build a simplified shopping basket which is made up of these components: a title and some products each of which contains a title and a remove button. Here is the HTML we might typically use:

	<div class="basket">
		<h2 class="basket-title">Basket</h2>
		<div class="basket-item">
			<h3 class="basket-productTitle">Product title</h3>
			<form>
				<input type="submit" class="basket-removeButton" value="Remove">
			</form>
		</div>
	</div>

And the selectors for that:

	/* module container */
	.basket {}

	/* components */
	.basket-title {}
	.basket-item {}
	.basket-productTitle {}
	.basket-removeButton {}

## Creating a second version of a module

Now, let's say that during the checkout process there is a similar (but different) cut down version of the basket&mdash;perhaps it has a title of "Order Summary" as opposed to "Your Basket". Perhaps it doesn't have the capability to remove products.

What you might be tempted to do, is to try and reuse the basket. But as we discussed in the chapter about Reuse, this is problematic for many reasons.

Additionally, your template or partial will require conditional logic within. The more condition you have, the more complicated it is to touch. And, whatever changes you make, might causes regression in *all* of the other places where it is used, making it hard to maintain.

Following the principle of duplication, it would be highly advised to create a brand new module. In a recent project, we named the module `.orderSummary` although interestingly it *looks* very similar to the basket it was a different module and trying to reuse styles would have caused pain.

Notice how with the code above we have ended up with Semantic naming and encapsulated styles making this very easy to maintain, upgrade or AB test as and when required without fear of regression elsewhere.
