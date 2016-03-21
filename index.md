---
layout: default
id: home
---

# Maintainable CSS

Warning: this is not even close to complete. I am commiting to live as I go. Who knows when this will be complete. Awww deadlins&mdash;oops a typo.

## Chapters

1. [Preface](#preface)
2. A note about semantics
3. How we begin
4. Working out what is a module
5. Writing a module
6. Etc

## Preface

A developer should be able to edit a module without affecting another. They should be able to develop a new module without inheriting overzealous, pre-existing styles that will ultimately result in lots of overrides.

There is no framwork to download and this is preprocessor agnostic. This is a set of guiding principles and conventions that allow you to write CSS in a way that gives you confidence, that the CSS you write will be maintainable and scalable.

### What does maintainable even mean?

It means I want to edit a module without having to worry that I have just fucked other modules on the site that I am not even aware of.

### What does scalable even mean?

This means when the CSS gets bigger, is it harder to edit existing code and add new code. If you have ever inherited a large CSS codebase I am sure you can sympathise with these problems.

## A note about semantics

It is said that the hardest parts of programming are naming and caching. So I don't wish to gloss over this point...

And semantics starts with the HTML. Let's begin there.

## How we begin

Resets, base styles

## Writing a module
