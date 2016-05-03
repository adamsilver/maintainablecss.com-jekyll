---
layout: chapter
title: Modifiers
section: Core
permalink: /chapters/modifiers/
description: Use modifiers to change appearance based on slight differences.
---

There are times when reusing the parts between curly braces makes total sense, in particular when a module (or component) is almost identical. 

**One example** I have experienced recently is an e-commerce site where each category page has a header at the top but the background image changes based on the category name as follows:

	<!-- when viewing the "boys" category page -->
	<div class="categoryHeader categoryHeader-boys"></div>

	<!-- when viewing the "girls" category page -->
	<div class="categoryHeader categoryHeader-girls"></div>

The CSS is identical, except for the `background-image` declaration based on the category.

**Another example** I experienced recently was on the product details page. We designed product pages so that depending on the colour of the product we could optionally change the background colour of the *Add To Basket* button.

	<!-- when viewing a product without a custom colour applied -->
	<input class="addToBasketButton">

	<!-- when viewing a product with a custom colour applied -->
	<input class="addToBasketButton addToBasketButton-green">

Too easy.