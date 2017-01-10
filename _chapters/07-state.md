---
layout: chapter
title: State
section: Core
permalink: /chapters/state/
description: Learn how to provide different styles to your modules and components based on state, such as showing, hiding and loading.
---

We may need to style elements differently when a module (or component) is in a particular state. Here some examples:

- showing or hiding
- active or inactive
- disabled or enabled
- loading or loaded
- hasProducts or hasNoProducts
- isEmpty or isFull

To apply different styling, we'll need to add an extra class onto the element. Here's both how you should and should not do this:

	<!-- Don't do this (Bad) -->
	<div class="thing isDisabled">

	<!-- Module level (Good) -->
	<div class="thing thing-isDisabled">

	<!-- Component level (Good) -->
	<p class="thing-blah thing-blah-isDisabled">

The reason for the prefix is because different elements may need different styles even though they have the same state. For example:

- a disabled *link* may have a dark background colour; but
- a disabled *basket* may have a greyed-out overlay.