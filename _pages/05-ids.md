---
layout: chapter
title: 5. A note about IDs
id: chapter5
permalink: /chapters/5/
previousPage:
  href: /chapters/4/
---

I don't know why as an industry we are so scared about using IDs. And don't get me wrong, I have read all the reasons but I still don't buy it.

First, we have to use IDs sometimes. Form controls are linked to labels via `id` and `for` attributes.

Second, an ID should be used to provide additional meaning to the developer. When I see an ID I know this thing is intended to be unique.

For example, I really don't see a problem and have never experienced a problem because I used an id of `header` for the header module that appears once on every page of the site.

In many ways, it's misleading to use a class name for a module that only ever appears once on a site. A class tells me that the intention of this module is such, that it can (and will) appear in multiple places.

With that said, just like the conventions I discussed earlier, this really doesn't matter too much.

Feel free to use only class names if that makes you feel better. I mention it because you're going to have to use IDs and you're better off being conscious about it so that you can reason about it and provide meaningful code.
