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

In a website the header, registration form, shopping basket, article, product list, navigation and homepage promo can all be considered to be modules.

## What's a component?

A module is made up of components. Without the components, the module is incomplete or broken.

For example a sofa is made up of the frame, upholstery, legs, cushions and back pillows, all of which are required components to allow the sofa to function as designed.

A logo *module* might consist of copy, an image and a link, each of which are components. Without the image the logo is broken, without the link the logo is incomplete.

## Modules vs components

Sometimes it's hard to decide whether something is a component or a module. For example, we might have a header containing a logo and a menu. Are these components or modules?

In a recent project of mine, it made sense for the logo to be a component and the menu to be a module of its own.

Nobody understands your requirements as well as you do. Through experience you'll get a feel for it. And if you get it wrong, changing from a component to a module (and vice versa) is easy.

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

## What about a module used in more than one place?

Our basket module only appears on the basket page. It requires less thinking about. But we didn't really address the fact that the remove button was a *component* of the basket.

Buttons are an example of something that we probably want to reuse in lot's of places, and potentially *within* different modules.

To do this, we could upgrade our component into a button module. The problem is that they often have different position, sizing and spacing depending on their context. And of course there is media queries to consider.

For example, in one module a button might be floated right within a container that has some text to the left of it. In another it might be centered with a fixed width and some text beneath with some bottom margin.

It's tricky to abstract the common rules because we don't want to end up in override hell. Or worse that we're afraid to update the abstracted set of CSS rules. If you still want to go ahead with this approach it looks like this:

	.primaryButton {
		/* Button styles */
	}

To avoid override hell, we can comma-delimit several buttons to apply the common rules that aren't affected by their context. For example:

	.basket-removeButton,
	.another-loginButton,
	.another-deleteButton {
      background-color: green;
      padding: 10px;
      color: #fff;
	}

Notice that in this example, we don't specify `float`, `margin` or `width` etc.

There's a third inbetweeny option. Imagine a checkout flow. On each page there's an identical continue button. Beside the continue button is a back link. We ended up with the following CSS:

	.checkoutActions-continueButton {
	  /*...*/
	}

	.checkoutActions-backButton {
	  /*...*/
	}

We abstracted the styles to a well understood set of modules, improving maintainability without affecting other similar (but not identical) buttons.