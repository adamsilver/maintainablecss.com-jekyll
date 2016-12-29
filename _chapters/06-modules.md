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

In a website each of these can be considered modules: header, footer, search form, sign up form, shopping basket, article, product list, navigation, homepage promo, archive list etc.

## What's a component?

A module is made up of components. Without the components, the module is incomplete or broken.

For example a sofa is made up of the frame, upholstery, legs, cushions and back pillows, all of which are required components to allow the sofa to function as designed.

A logo *module* might consist of copy, an image and a link, each of which are components. Without the image the logo is broken, without the link the logo is incomplete.

## Modules vs components

Sometimes it's hard to decide whether something is a component or a module. For example, you might have a header module containing a logo and a menu. Are these components or modules?

In a recent project of mine, it made sense for the logo to be a component of the header. But the menu was a module within it.

Ultimately, nobody understands your requirements as well as you do. Through experience you'll get a feel for it. And if you get it wrong, changing from a component to a module (and vice versa) is easy.

## Creating a module

Let's build a shopping basket module together, which I have simplified for brevity. Each product contains a title and a remove button. The HTML might be as follows:

	<div class="basket">
	    <h2 class="basket-title">Your Basket</h2>
	    <div class="basket-item">
	        <h3 class="basket-productTitle">Product title</h3>
            <form>
                <input type="submit" class="basket-removeButton" value="Remove">
	        </form>
	    </div>
	</div>

And the selectors for that might be:

	/* module container */
	.basket {}

	/* components */
	.basket-title {}
	.basket-item {}
	.basket-productTitle {}
	.basket-removeButton {}

## Creating a second version of a module

Now imagine that there's a cut-down version of the basket shown during checkout. It is titled "Order Summary" instead of "Your Basket" and users cannot remove a product.

### Don't reuse

You may be tempted to reuse the HTML and CSS because it looks similar. But resist this temptation. If you do this then:

* you'll need to add display logic to manage the differences. This is relatively hard work; and
* you may need CSS overrides to acheive the two layouts using one template; and
* the added complexity increases the chance of regression.

Instead of trying to reuse, duplicate the module and remove the differences.

### Create two modules instead

In a recent project, I named the new version `.orderSummary`. There were similarities but some differences too. This was enough to make duplication a much better prospect.

Also, it's not really duplication. Duplication is copying the *same* thing. These two modules might *look* similar but they are not the same.

We've encapsulated the styles to the module. This means we can edit the Basket without causing regression in the Order Summary. Our life is much easier this way.
