---
layout: chapter
title: Introduction
section: Preface
---

*MaintainableCSS* is an approach to writing CSS that helps you, your current team and your future team to maintain CSS.

## What is the goal of *MaintainableCSS*?

If I had to sum up the overarching goal of *MaintainableCSS* in one paragraph it would be as follows:

**To ensure that as a developer, I can edit an existing feature (or add a new one) to the codebase without worrying that overzealous, pre-existing styles will cause a problem for me or that I will cause regression elsewhere.**

## There is nothng to download

*MaintainableCSS* is not something you can download. It's a set of principles, guides and conventions that not only allow you to write CSS with piece of mind, but that also means your CSS is maintainable and scalable.

## What does maintainable even mean?

It means I want to edit a module without having to worry that I have just fucked other modules on the site that I am not even aware of. It also means that if I write some new code, then my first job *isn't* to override a bunch of styles that I have just inherited. It also means that I can edit existing styles with confidence that I won't cause an unexpected regressions elsewhere.

## What does scalable even mean?

This means that when the CSS increases in size, it *doesn't* make the maintaining of code (see above) any harder. If you have ever inherited a large, unmaintainable CSS codebase, I am sure you can sympathise with these problems.

## What does modular even mean?

A module is a distinct, indepenent unit, that can be combined with other modules to form a more complex structure. In a living room, you can consider the TV, the sofa and the wall art modules. All coming together to create a useable room.

If you take one of the units away, the rest still works just fine. I don't need any aspect of the TV to be able to sit on the sofa. Okay you get the picture :)

## Who is this for?

These conventions are useful for tiny projects with 1 person on the team and equally they are useful for huge projects with 100 people on the team. And whether your design is set in stone for the next 5 years or will evolve frequently, *MaintainableCSS* can help.
