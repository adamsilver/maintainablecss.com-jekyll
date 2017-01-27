---
layout: chapter
title: Javascript
section: Extras
permalink: /chapters/javascript/
description: How to write maintainable CSS and maintainable Javascript at the same time.
---

We may want to use Javascript to apply the same behaviour to multiple modules or components.

For example, we may use a `Collapser` constructor that toggles an element's visibility.

There are two approaches we can take. Both of which compliment the CSS approach we've discussed in previous chapters.

## 1. Encapsulating state to the module

To do this, we would need to specify a module-specific state class to the constructor as follows:

	var module1Collapser = new Collapser(element1, {
	  cssHideClass: 'moduleA-isHidden'
	});

	var module2Collapser = new Collapser(element2, {
	  cssHideClass: 'moduleB-isHidden'
	});

Then reuse the CSS styles as follows:

	.moduleA-isHidden,
	.moduleB-isHidden {
      display: none;
	}

The trade-off is that this list could grow quickly. And everytime we add behavior, we need to update the CSS. A small change, but a change nonetheless. In this case we might consider a global state class.

## 2. Creating a global state class

If we find ourselves repeating the exact same set of styles for multiple modules, it might be better to use a global state class as follows:

	.globalState-isHidden {
      display: none;
	}

This approach does away with the long comma-delimitted list. And we no longer need to specify the module class when instantiating. This is because the global class will be referenced from within.

	var module1Collapser = new Collapser(element1);
	var module2Collapser = new Collapser(element2);

However, this approach doesn't always make sense. We may have two different modules that *behave* the same, but *look* different, which is something we've discussed in [State](/chapters/state/).

Lastly, we could always default to this approach and if we need to specify a class, just pass it into the constructor as shown in the first example above.



<!-- display: flex vs display: block -->