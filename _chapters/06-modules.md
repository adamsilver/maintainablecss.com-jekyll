---
layout: chapter
title: Modules
---

A module is a section of the page that represents a piece of functionality in it's own right.

For example a search feature residing within the header might be a module.

The *header* itself might be a module made up of other modules such as *logo*, *navigation* and the aformentioned *search* module.

Some might try to differentiate between a module and a modules that reside within a module but I don't think it's worth differentiating&mdash;it's a mental burden which I don't think helps the [goal of *Maintainable CSS*](/chapters/1/).

You will see what I mean when we carry out some examples together and ultimately you can decide if a module within a module in it's own right or a component of that module. You will see it doesn't matter too much.

## Identifying a module from the visual design

Coming soon.

## Example: Shopping basket

	.basket {}

	.basket-title {}

	.basket-item {}

	.basket-removeButton {}

Now let's say that we now had a mini basket throughout the checkout process. So there was a basket on the checkout and it looked different and was a cut down summary version&mdash;for exmaple there was no remove button. We have lot's of options. It could be known as `orderSummary` or it might be `basketSummary` or `miniBasket`.

All of these names are semantic, all of these names are module friendly and unique. So pick whatever you prefer after you have given it some thought.

On a project I was recently on we ended up with `orderSummary`.

	.orderSummary {}

	.orderSummary-title {}