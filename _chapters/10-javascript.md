---
layout: chapter
title: Javascript
section: Extras
permalink: /chapters/javascript/
description: What does MaintainableCSS suggest when it comes to Javascript? Find out in this chapter.
---

Sometimes you have two completely different modules but they both have the same behaviour applied through Javascript. A rudimentary example would be two modules (or components for that matter) have the same state *isHidden* which equates to a `display: none`.

How should you handle this without losing the best practice MaintainableCSS guides described in previous chapters, without repeating the same CSS code in every module state class?

There are two approaches you can take.

## 1. Reusing the same styles across modules

If you have a constructor that is responsible for making an element show (or hide) then I would consider specifying the specific module class names during instantiation:

	var module1Collasper = new Collapser(element1, {
	    cssHideClass: 'moduleA-isHidden'
	});

	var module2Collapser = new Collapser(element2, {
	    cssHideClass: 'moduleB-isHidden
	});

Then I would likely reuse the CSS styles as follows:

	/* isHidden */
	.moduleA-isHidden,
	.moduleB-isHidden {
		display: none;
	}

However, if you find this approach causes maintainability issues for whatever reason then you could try an alternative approach.

## 2. Add a global state class

If you find the first approach causes maintainability issues then it might be better to define a global state class for reuse across different modules:

	.globalState-isHidden {
	    display: none;
	}

In this scenario, you no longer need to comma delimit each module state, and you no longer need to specify the module state class during instantiation:

	var module1Collasper = new Collapser(element1);
	var module2Collasper = new Collapser(element2);

Whilst this approach might *seem* to be more maintainable due to less code to update, it does require thought and care which in turn can be problematic in terms of maintainability.

For example it might be that there are other visual differences specific to each module that hang off the *isHidden* state class. If there are any differences at all, I would factor it out in order to make the code easy to reason about, and to update without causing unexpected regression.

<!-- display: flex vs display: block -->