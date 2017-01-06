---
layout: chapter
title: Javascript
section: Extras
permalink: /chapters/javascript/
description: How to write maintainable CSS and maintainable Javascript at the same time.
---

You may want to use Javascript to apply the *same* behaviour to multiple modules (or components). A basic example would be two modules that have the same *isHidden* state which hides the module.

How might we do this whilst adhering to these guides and without having to repeat ourselves?

There are two approaches you can take.

## 1. Encapsulating state to the module

If you have a constructor that is responsible for making an element toggle visibility then consider specifying a class name that pertains to the module during instantiation:

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

You might find that this list gets rather large. In which case you might decide to abstract this style into a global state class.

## 2. Creating a global state class

As discussed above, you might prefer to use a global state class which is applicable *across* modules.

	.globalState-isHidden {
      display: none;
	}

This approach does away with the long comma-delimitted list. And you no longer have to specify the module class when instantiating. This is because the global class will be referenced from within.

	var module1Collapser = new Collapser(element1);
	var module2Collapser = new Collapser(element2);

This may seems more maintainable because there's less code to update. But it does require your careful consideration.

For example, there might be other visual differences specific to each module that hang off the *isHidden* class. If there are differences, it's probably better to go with the first approach.

<!-- display: flex vs display: block -->