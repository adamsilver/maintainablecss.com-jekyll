---
layout: chapter
title: State
section: Core
permalink: /chapters/state/
description: Learn how to provide different styles to your modules and components based on state, such as showing, hiding and loading.
---

Quite often, particularly with richer user interfaces, styling needs to be applied in response to an element's change of state. For example, we may have different styles when a module (or component) is:

- showing or hiding;
- active or inactive;
- disabled or enabled;
- loading or loaded;
- hasProducts or hasNoProducts;
- isEmpty or isFull;

To represent state we need an additional class which should be added to the module (or component) element to which it pertains. For example, if our basket module needs a gray background when it's empty, the HTML should be:

	<div class="basket basket-isEmpty">

And the CSS should be:

	.basket-isEmpty {
      background-color: #eee;
	}

The class name is prefixed with the module (or component) because whilst states might be common, associated styles might not. For example, an empty *basket* has a gray background, where as an empty search has an absolutely-positioned image.

## What about reusing state?

Sometimes, we may in fact want to reuse state across modules or components. For example, toggling an element's visibility. This is discussed in more detail in the chapter entitled [Javascript](/chapters/javascript/).

## What about ARIA attributes?

Not all visual states can be represented by an [ARIA attribute](https://www.w3.org/TR/wai-aria/states_and_properties#attrs_widgets). For example, there is no attribute to represent `hasProducts`. Therefore, we should use them only when necessary and in *addition* to classes.

Also, using an attribute (instead of a class) selector has [less support](https://www.impressivewebs.com/attribute-selectors/). Whilst developers may consider these browsers old, insecure or irrelevant, we should avoid techniques that may exclude users.

## Final thought

If we need to style an element based on state apply an extra class. When necessary, use ARIA in addition to a class, to avoid techniques that unnecessarily exclude users.
