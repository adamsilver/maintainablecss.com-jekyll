---
layout: chapter
title: Modifiers
section: Core
permalink: /chapters/modifiers/
description: Use modifiers to change appearance based on slight differences.
---

Modifiers are similiar to states in that they can change or override the style of a module. This can be useful when modules (or components) are almost identical but have slight differences as designed.

When this is the case, reusing or abstracting common CSS rules is useful for maintainability. This is best explained with two examples:

## Example 1: Different background images

One recent example I have is for an e-commerce site where each Category page has a header at the top but the background image changes based on the category name as follows:

	<!-- when viewing the "boys" category page -->
	<div class="categoryHeader categoryHeader-boys">

	<!-- when viewing the "girls" category page -->
	<div class="categoryHeader categoryHeader-girls">

The CSS for each header is almost identical except for the modifier overrides:

	.categoryHeader {
	    padding-top: 50px;
	    padding-bottom: 50px;
	    /* etc */
	}

	.categoryHeader-boys {
	    background-image: url(/path/to/boys.jpg);
	}

	.categoryHeader-girls {
	    background-image: url(/path/to/girls.jpg);
	}

## Example 2: Different colour buttons

In the same site we designed Product pages so that depending on the colour of the product, we could optionally configure the background colour of the *Add To Basket* button to match, in the CMS.

	<!-- when viewing a product with a green colour applied -->
	<input class="addToBasketButton addToBasketButton-green">

The CSS for the green button is identical except for the background-color as follows:

	.addToBasketButton {
	    padding: 10px 30px;
	    text-align: center;
	    /* etc */
	}

	.addToBasketButton-green {
	    background-color: green;
	}

Easy.