---
layout: chapter
title: Modules
section: Core
permalink: /chapters/modules/
description: Learn the differences between modules and components and how to identify them within a design. We'll also code up some example modules together.
---

## What's a module?

A module is a distinct, independent unit, that can be combined with other modules to form a more complex structure.

In a living room, you can consider the TV, the sofa and the wall art modules. All coming together to create a useable room.

If you take one of the units away, the rest still works just fine. I don't need the TV to be able to sit on the sofa etc.

**In a website each of these can be considered modules:** header, footer, search form, sign up form, shopping basket, article, product list, navigation, homepage promo, archive list etc.

## What's a component?

A module is made up of components. Without the components, the module is incomplete or broken.

For example a sofa is made up of the frame, upholstry, legs, cushions and back pillows, all of which are required components to allow the sofa to function as designed.

A logo *module* might consist of copy, an image and a link, each of which are components. Without the image the logo is broken, without the link the logo is incomplete.

## Modules vs components

Sometimes it can be tricky to decide whether something is a component or a module. For example a header is a module and it might contain a logo and a navigation menu as part of it. Are these components or modules?

Ultimately it doesn't matter too much and you can use your own experience to decide. For me, in a recent project it made sense for the logo to be a component of the header, and the navigation menu to be a module within the header.

Ultimately, only you understand *your* project requirements and if you get this wrong, changing a component for a module or vice versa is a very easy thing to do.

## Creating a module

Let's build a module together. We're going to build a simplified shopping basket which is made up of a title and some products each of which contain the product title and a remove button. Here is the HTML we might typically use:

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

That was straight forward.

## Creating a second version of a module

Now, let's say that during the checkout process there is a similar, cut-down version of the basket&mdash;perhaps it has a title of "Order Summary" as opposed to "Your Basket". And perhaps it doesn't have the capability to remove products.

### Don't be tempted to reuse

You might be tempted to try and reuse the basket, but as we have learnt in the chapter about Reuse, this is problematic for many reasons.

Additionally, your template or partial will require conditional logic to handle the differences. The more conditionality you have, the more complicated it is to touch. And, due to this conditionality, the changes you make to the template might cause regression in a condition you're not currently testing, making it harder to maintain.

### Duplicate duplicate duplicate

*MaintainableCSS* of course, advises to duplicate the module instead. In a recent project, I named the new version `.orderSummary`. There was similarities but just a few differences was enough to duplicate instead of the pain of trying to reuse.

Finally, notice how with the CSS above, we have ended up with Semantic naming and encapsulated styles, making this very easy to maintain, upgrade or AB test, as and when required without fear of regression elsewhere.
