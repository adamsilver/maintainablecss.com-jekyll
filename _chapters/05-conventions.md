---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

*MaintainableCSS* has the following convention:

	.<module>[-<component>][-<state>] {}

Square brackets are optional depending on the module in question. Here are some examples:

	/* Module container */
	.searchResults {}

	/* Component */
	.searchResults-heading {}

	/* State */
	.searchResults-isLoading {}

Notes:

- component and state are both delimited by a dash
- names are written with lowerCamelCase
- selectors are prefixed with the module name

## Must I give a class name to every element?

No. You can write `.searchResults p` if you want to. And sometimes you may have to, if for example you're using markdown. But beware that if you nest a module which contains a `p` it will inherit the styles and need overriding.

## Why must I prefix the module name?

Good question. Here's some HTML without a prefix:

	<div class="basket">
	  <div class="heading">

And the CSS:

	/* module */
	.basket {}

	/* heading component of basket module */
	.basket .heading {}

There are two problems:

1. when viewing HTML, it's hard to differentiate between a module and a component; and
2. the `.basket .heading` component will inherit styles from the `.heading` module which has unintended side effects.
