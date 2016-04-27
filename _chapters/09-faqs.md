---
layout: chapter
title: Frequently Asked Questions
section: Extras
permalink: /chapters/faqs/
description: Common questions answered
---

## What about if I want to prototype something quickly?

MaintainableCSS is important for production quality CSS. If you're building something really quickly just for test purposes, feel free to use what you like.

## Why do I need to prefix components with the module name?

I actually used to write HTML like this:

	<div class="basket">
		<div class="heading">
		</div>
	</div>

And CSS like this:

	/* basket module */
	.basket {}

	/* basket heading component */
	.basket .heading {}

The problem comes when a component name matches the name of a module. By the convention above there is no differentiation between a component and a module. Imagine we have a module called "heading":

	/* heading module */
	.heading {}

In this case the `.basket .heading` *component* will incorrectly inherit the styles from the `.heading` *module*.

"ieading" and "item" and many other words are meaningful to lots of different modules and components across a website but they might also be names for the module itself. Follow MaintainableCSS [conventions](/chapters/conventions/) means you avoid this problem.

## What about common styles that you use across different modules e.g. buttons?

In the chapter about [Modules](/chapters/modules/) there is a component defined as `.basket-removeButton` but what if the styling for that is used in many places?

There are two approaches. Firstly, you can create a `buttons.css` file and have the following section:

	/***********************************
	* Button style for primary actions
	***********************************/

	.basket-removeButton,
	.another-loginButton,
	.and-anotherDeleteButton {
		/*common styles*/
	}

Or you can just have a button as a module:

	.primaryButton {
		/* common styles */
	}

There is nothing wrong with having a module within a module. You just have to be careful with the latter approach, because once you edit a style it propagates everywhere, and this can be problematic due to unexpected regression.

## What about reusing common Javascript behaviour such as showing and hiding?
<!--https://github.com/adamsilver/maintainablecss.com/issues/20-->

Let's say you have 2 modules, Module A and Module B. Each of them look completely different, are completely different except they both have a collapsed state. Normally you would have some script that adds and removes the class in order to implement this.

The first way is to have an option inside the Collapser Javascript component as follows:

	var collapser1 = new Collapser(el, { cssHideClass: 'moduleA-isHidden' });
	var collapser2 = new Collapser(el, { cssHideClass: 'moduleB-isHidden });

The CSS might be:

	/* hidden */
	.moduleA-isHidden,
	.moduleB-isHidden {
		display: none;
	}
	
If this becomes painful then you could consider a global state as follows:

	.globalState-isHidden {
		display: none;
	}

Then the Javascript is as follows:

	var collapser1 = new Collapser(el});
	var collapser2 = new Collapser(el);

Whilst this latter one, might at first appear to be more maintainable, you have to be careful doing this. It might be that you want to drive other styles from this class. But what applies to one module may not apply to the other. 

Which leads to the last option of prefixing Javascript related behaviour with a prefix of "js-".