---
layout: chapter
title: Modules
section: Core
permalink: /chapters/modules/
---

A module is a distinct, independent unit, that can be combined with other modules to form a more complex structure.

In a living room, you can consider the TV, the sofa and the wall art modules. All coming together to create a useable room.

If you take one of the units away, the rest still works just fine. I don't need the TV to be able to sit on the sofa etc.

**In a website each of these can be considered modules:** header, footer, search form, sign up form, shopping basket, article, product list, navigation, homepage promo, archive list etc.

## Modules vs components

A module is made up of components. Without the components the module is incomplete or broken.

For example a sofa is made up of the frame, upholstry, legs, cushions and back pillows. These are all required components to make the sofa function as desired.

With all of this said, sometimes it can be tricky to decide whether something is a component or something is a module. For example a header is a module. It might contain a logo and a navigation menu as part of it.

Are these components or modules? Ultimately it doesn't matter too much and you can use you're own experience to decide. For me, in a recent project it made sense for the logo to be a component of the header, and the navigation menu to be a module within the header module.

Regardless, *MaintainableCSS* doesn't force anything because it doesn't know *your* project requirements. I merely address this point because sometimes we can get hung up on these things and most of the time, it is very clear what a module is.

And all said and done, it's very easy to change your mind and swap a component for a module as the conventions are so simple.

## Walkthrough: creating a module

Let's build a module together. We're going to build a simplified shipping basket module which is made up of a title, a bunch of products with each product containing a title and a remove button. Here is the HTML we might typically use:

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

## Walkthrough: avoiding reuse

Now, let's say that during the checkout process there is a similar (but different) cut down version of the basket&mdash;perhaps it has a title of "Order summary" as opposed to basket. Perhaps it doesn't have the capbility of removing products.

What you might be tempted to do, is to try and reuse the basket. But as we discussed in the chapter about Reuse, this is problematic for several reasons.

Additionally, your template or partial will require conditional logic within. The more condition you have, the more complicated it is to touch. And, whatever changes you make might causes regression in *all* of the other places where it is used, making it hard to maintain.

Following the principle of *duplication first*, it would be highly advised to create a brand new module. In a recent project, we named the module *orderSummary* although interestingly it *looks* very similar to the basket.

Now we have semantic naming, module encapsulation which makes maintainance very easy. If the design is changed for just one of these modules we can upgrade with minimal effort and without fear of regression.