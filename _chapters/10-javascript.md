---
layout: chapter
title: Javascript
section: Extras
permalink: /chapters/javascript/
description: How to write maintainable CSS and maintainable Javascript at the same time.
---

You may want to use Javascript to apply the *same* behaviour to multiple modules (or components). A basic example would be two modules that have the same *isHidden* state which hides the module.

**How might you do this whilst adhering to MaintainableCSS guidelines and without having to repeat yourself?**

There are two approaches you can take.

## 1. Encapsulating states to the module

If you have a constructor that is responsible for making an element show (or hide) then consider specifying a class name that pertains to the module during instantiation:

	var module1Collasper = new Collapser(element1, {
	  cssHideClass: 'moduleA-isHidden'
	});

	var module2Collapser = new Collapser(element2, {
	  cssHideClass: 'moduleB-isHidden'
	});

Then reuse the CSS styles as follows:

	/* isHidden */
	.moduleA-isHidden,
	.moduleB-isHidden {
      display: none;
	}

However, if you find this approach causes maintainability issues for whatever reason then you could try an alternative approach...

## 2. Creating a global state class

If you find the first approach causes maintainability issues then it might be better to define a global state class for reuse across different modules:

	.globalState-isHidden {
      display: none;
	}

In this scenario, you no longer need to comma delimit each module state, and you no longer need to specify the module state class during instantiation as the `Collapser` constructor will reference the global class name from within:

	var module1Collasper = new Collapser(element1);
	var module2Collasper = new Collapser(element2);

Whilst this approach might *seem* to be more maintainable due to there being less code to update, it does require thought and care which in turn can be problematic.

For example it might be that there are other visual differences specific to each module that hang off the *isHidden* class. If there are any differences at all, it may well be better to go with the first approach described above as it's easier to reason about and update without causing unexpected regression.

<!-- display: flex vs display: block -->