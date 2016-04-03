---
layout: chapter
title: Modules
section: Core
permalink: /chapters/modules/
---

*A module is a distinct, indepenent unit, that can be combined with other modules to form a more complex structure. In a living room, you can consider the TV, the sofa and the wall art, modules. All coming together to create a useable room.*

## What could be a module?

Here are 10 examples of a module:

1. Header
2. Footer
3. Search Form
4. Sign up form
5. Shopping basket
6. Article
7. Product list
8. Navigation
9. Filter
10. Homepage promotional item.

## Modules vs components

As we have just seen, a *module* is something useful in it's own right. But also, a module is made up of bits and pieces that make it useful.

For example, a piece of wall art is made up of a frame, a picture, the glass and the nail. Without these pieces it renders the module useless. These pieces are what I call *components*.

Sometimes, it can be difficult to make a choice between whether something is a module or a component. For example, the header might be a module. The header might contain a logo, a navigation and a global search form.

It could be argued that the logo is a component of the header. Because without the logo, the header provides no value and that it needs the container in order to position it to (typically) the top left of the header.

But equally, the logo is valuable in it's own right and could easily be considered a module (within a module). Either way that is no problem. *MaintainableCSS* doesn't concern itself. That choice is up to you.

And also, it makes sense that navigation might reside in the header, but it is most certainly a useful independent unit regardless of the header.

And it must be noted that, the visual design might have an impact in what becomes a module. For example the navigation might be positioned to the right of the header with a `float: right` but it is visually positioned in a header module. The header module will 'clear' the float.

In this particular example, I would *still* make the navigation a module itself. It's just a module within a module. No problem, and again don't worry too much. It is very easy to convert a component into a module and vice versa.

## Let's create a module: Shopping basket

Let's take a simple example, a shopping basket. Typically, a basket contains a title, a bunch of items, each item might have a remove button. So we might end up with the following HTML:

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

Now, let's say that during the checkout process there is a similar (but different) cut down version of the basket&mdash;perhaps it has a title of "Order summary" as opposed to basket. Perhaps it doesn't have the capbility of removing products.

What you might be tempted to do, is to try and reuse the basket. But as we discussed in the chapter about Reuse, this is problematic. Firstly, you're template/partial will require conditional logic within.

The more condition you have, the more complicated it is to touch (read: maintain). And, now whatever changes you make might causes issues in *all* of the places where it is used.

Following the principle of *duplication first*, it would be highly advised to create a brand new module. In a recent project, we named the module *orderSummary*. We could have easily named it *basketSummary* or *checkoutBasket* or *basketCutDownVersion*.

Now, the name *is* important &mdash; it must be semantic &mdash; which all of these are. But, even *more* important, is the fact that a new module has been created, rather than trying to reuse the existing similar module.

We have now acheived the ability to style this new module as we wish, whilst also being able to edit the other basket module, without fear of regression or inheriting other styles we don't want.

If the design changes, upgrading these modules is now very easy to do.