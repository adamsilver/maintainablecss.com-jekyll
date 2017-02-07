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

If we take one of the units away, the others still work. We don't need the TV to be able to sit on the sofa etc.

In a website the header, registration form, shopping basket, article, product list, navigation and homepage promo can all be considered to be modules.

## What's a component?

A module is made up of components. Without the components, the module is incomplete or broken.

For example a sofa is made up of the frame, upholstery, legs, cushions and back pillows, all of which are required components to allow the sofa to function as designed.

A logo *module* might consist of copy, an image and a link, each of which are components. Without the image the logo is broken, without the link the logo is incomplete.

## Modules vs components

Sometimes it's hard to decide whether something should be a component or a module. For example, we might have a header containing a logo and a menu. Are these components or modules?

In a recent project it made most sense for the logo to be a component and the menu to be a module of its own. What's a header without logo? And the navigation might be moved below the header.

Nobody understands your requirements as well as you do. Through experience you'll get a feel for it. And if you get it wrong, changing from a component to a module is easy.

That's enough theory. Let's build three different modules together. In doing so, the hope is to cover most of the things we think about when writing CSS.

## 1. Creating a basket module

We'll simplify this basket for brevity. Each product within the basket will display the product's title with the ability to remove it from the basket.

The basket template might be:

	<div class="basket">
	  <h1 class="basket-title">Your basket</h1>
	  <div class="basket-item">
	      <h3 class="basket-productTitle">Product title</h3>
          <form>
              <input type="submit" class="basket-removeButton" value="Remove">
	      </form>
	  </div>
	</div>

And the CSS would be:

	.basket {}
	.basket-title {}
	.basket-item {}
	.basket-productTitle {}
	.basket-removeButton {}

## 2. Creating an order summary module

Next, we will build an order summary module. This module is shown during checkout and bears some resemblance to the basket. For example, it has a title and it displays a list of products.

It does, however, have a different aesthetic and the products can no longer be removed i.e. no form and no remove button.

The first thing to address is the temptation to reuse the basket template (and CSS). Even though there are similarities, this does not mean they are the same.

If we try to combine them we'll entangle two modules with display logic and CSS overrides. This entangling by definition is complex which in turn is hard to maintain and easily avoidable.

Instead, we should create a new module with the following template:

	<div class="orderSummary">
	  <h2 class="orderSummary-title">Order summary</h2>
	  <div class="orderSummary-item">...</div>
	  <div class="orderSummary-item">...</div>
	</div>

And the CSS would be:

	.orderSummary {}
	.orderSummary-title {}
	.orderSummary-item {}

As counterintutive as this may seem, duplication is a better prospect. And, this is not really duplication. Duplication is copying the *same* thing. These two modules might look similar but they are not the same.

Keeping things separate, keeps things simple. Simple is the most important aspect of building reliable, scalable and maintainable software.

## 3. Creating a button module

As our basket module only appears in the basket page, we didn't consider being able to reuse it elsewhere. Also, we didn't address the fact that the remove button is a component of the basket, making them harder to reuse across modules.

Buttons are an example of something that we want to reuse in lot's of places, and potentially *within* different modules. A button is not particularly useful on its own.

One option would be to upgrade the button component into a module as follows:

	<input class="primaryButton" type="submit" value="{%raw%}{{text}}{%endraw%}" ...>

And the the CSS would be:

	.primaryButton {}

The problem is that different buttons often have slightly different positioning, sizing and spacing depending on context. And of course there is media queries to consider.

For example, within one module a button might be floated to the right next to some text. In another it might be centered with some text beneath with some bottom margin.

Because of this, it's tricky to abstract the common rules because we don't want to end up in override hell. Or worse that we're afraid to update the abstracted CSS rules.

To avoid these problems, we can use a mixin or comma-delimit the common rules that aren't affected by their context. For example:

	.basket-removeButton,
	.another-loginButton,
	.another-deleteButton {
      background-color: green;
      padding: 10px;
      color: #fff;
	}

Notice that in this example, we don't specify `float`, `margin` or `width` etc. Those styles are applied to the unique button:

	.basket-removeButton {
	  float: right;
	}

	.another-deleteButton {
	  margin-bottom: 10px;
	}

There's a third option. Imagine a checkout flow whereby each page has a continue button and a link to the previous step. We can again reuse it by upgrading it into a module:

	<div class="checkoutActions">
	  <input class="continue" ...>
	  <a class="checkoutActions-back" ...></a>
	</div>

And the CSS would be:

	.checkoutActions-continue { }

	.checkoutActions-back { }

In doing this, we have abstracted and applied the styles to a well understood `.checkoutActions` module. And we've done this without affecting similar, but not identical buttons.

We haven't discussed having more than one type of button yet. To do this we can use modifiers, which is addressed later.

## Final thought

Modules allow us to reuse HTML and CSS across a website. By definition a module is reusable. Before something can be upgraded into a module, we must first understood what it is and what the different use cases are.

Once we do, we can abstract the HTML and styling accordingly. With careful thought we can make the right abstraction and avoid complexity at the same time.