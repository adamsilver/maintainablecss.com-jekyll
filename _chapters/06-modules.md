---
layout: chapter
title: Modules
section: Core
permalink: /chapters/modules/
description: Learn the differences between modules and components and how to identify them within a design. We'll also code up some example modules together.
---

## What's a module?

A module is a distinct, independent unit, that can be combined with other modules to form a more complex structure.

In a living room, we can consider the TV, the sofa and the wall art modules. All coming together to create a useable room.

If we take one of the units away, the rest still works just fine. We don't need the TV to be able to sit on the sofa etc.

In a website each of these can be considered modules: header, footer, search form, sign up form, shopping basket, article, product list, navigation, homepage promo, archive list etc.

## What's a component?

A module is made up of components. Without the components, the module is incomplete or broken.

For example a sofa is made up of the frame, upholstery, legs, cushions and back pillows, all of which are required components to allow the sofa to function as designed.

A logo *module* might consist of copy, an image and a link, each of which are components. Without the image the logo is broken, without the link the logo is incomplete.

## Modules vs components

Sometimes it's hard to decide whether something is a component or a module. For example, we might have a header containing a logo and a menu. Are these components or modules?

In a recent project of mine, it made sense for the logo to be a component and the menu to be a module of its own.

Ultimately, nobody understands your requirements as well as you do. Through experience you'll get a feel for it. And if you get it wrong, changing from a component to a module (and vice versa) is easy.

## Creating a module

Let's build a *basket* module which we'll simplify for brevity. Each product contains a title and a remove button. The HTML might be:

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

Now imagine that there's an *order summary* module shown during checkout. It it similar to the basket, in that it contains a list of products.

### Don't reuse

We may be tempted to reuse the basket HTML template and CSS because it bares some resemblance. It would be wise not to do this, otherwise we'll have to add:

* display logic to manage the differences; and
* CSS overrides to styles the two modules using one template.

This intertwining of modules by definition is complex. This complexity is hard to maintain.

### Split into two modules

Instead create another module and name it `.orderSummary`. As counterintutive as it may seem, duplication is a much better prospect.

Also, it's not really duplication. Duplication is copying the *same* thing. These two modules might *look* similar but they are not the same.

Keeping things separate, keeps things simple. Simple is the most important aspect of building reliable, scalable and maintainable software.
