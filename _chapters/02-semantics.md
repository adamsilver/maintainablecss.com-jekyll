---
layout: chapter
title: Semantics
section: Background
permalink: /chapters/semantics/
description: Why naming something based on what it is, instead of how it looks or behaves is a cornerstone of writing well architected and maintainable CSS code.
---

Summary: Name something based on what it *is*, not how it *looks* or *behaves*.

## The longer explanation

Semantic HTML isn't just about the elements we use. It's quite obvious that we should use `<a>` for links, `<table>` for tabular data and `<p>` for paragraphs etc.

What's not quite so obvious is the values we use for classes. This is important because they enable us to enhance a web page with style (and behaviour).

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

It's important to name elements well. We humans aren't so good at understanding abbreviated, non-semantic abstractions.

## Good and bad class names

Here are some examples of semantic and non-semantic class names:

	<!-- non semantic -->
	<div class="red pull-left">
	<div class="grid row">
	<div class="col-xs-4">

	<!-- semantic -->
	<div class="basket">
	<div class="product">
	<div class="searchResults">

Non semantic classes don't tell us *what* the HTML represents. At most, they give us an idea of what elements look like.

Semantic classes have a much clearer meaning. They don't tell us what they look like, but that's okay. That's what CSS is for. Semantic class names mean something to HTML, CSS, Javascript and automated tests.

There are many reasons why semantic class names are advantageous:

## 1. Because their intention is clear

The intention of a semantic class name is clear, whether we're looking at the HTML or the CSS. Understanding the intention of an element when it has a sprinkling of visual classes is far less clear. At most we'll gain a vague understanding of the stylistic intentions.

## 2. Because it's easier to build responsive sites

Styles often change in response to screen size. For example, elements may sit beside each other when there's enough space. When there isn't they'll be stacked.

When the elements are stacked, a `clearfix` class, for example, is redundant and makes for misleading code. *Semantic* class names enable us to style elements easily through media queries.

## 3. Because they are easier to find

Many elements will use `.red` and `.pull-left` classes. Therefore, a search will yield many results. This means it will be hard to track down the HTML in question.

A semantic class, such as `.basket`, should yield just one result making it much easier to find. And if we inspect an element, it will be quicker to track down the releated selector.

## 4. Because they reduce the risk of regression

Updating a visual class name increases the chance of regression. This is because many elements will use them. It will take a lot of time and effort to check otherwise.

As semantic class names are unique, we can be confident that are changes only apply to the module in question. This makes them easier to maintain.

## 5. Because we want to make changes with confidence

When we don't feel confident changing code, we either cause problems or we  avoid doing the work which creates redundancy.

## 6. Because they provide hooks for automated tests too

Automated functional tests work by searching for and interacting with elements. This may include:

1. clicking a link;
2. finding a text box;
3. typing in text;
4. submitting a form; and then
5. verifying some criteria.

Visual class names don't allow us to target specific elements because they apply to many. Adding hooks just for tests is foolhardy.

## 7. Because they provide hooks for Javascript too

Semantic class names are useful for Javascript too. We can't use visual class names as a reliable way to retrieve elements.

## 8. Because they don't need maintaining

If we name something based on what it is, we won't have to update the HTML again. A heading is always a heading, no matter what it *looks* like.

The styling might change but this only requires a CSS update. This is known as Loose Coupling which improves maintainability.

## 9. Because they are easier to debug

It's harder to inspect an element with a multitude of visual class names. With a semantic class there will be just one.

## 10. Because the standards recommend it

On using the class attribute, HTML5 specs say in 3.2.5.7:

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

## 11. Because they encourage lean HTML

When we use semantic class names, the HTML will be smaller. The CSS might get bigger but it's cacheable.

<!--## Because visual class names might declare the same property!

It's likely that several different utility classes could refer to the same property meaning order matters and performance degrades.

Think of an example of this.
-->

## End note

Semantic class names are a corner stone of *MaintainableCSS*. Without them, everything else makes little sense. So name something based on what it is and everything else falls into place.
