---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/javascript/
description: What does MaintainableCSS suggest when it comes to Javascript? Find out in this chapter.
---

For example: There are 2 Modules used. Module-A and Module-B. Both will have the same state "isHidden" with exact the same css-code (display:none). 
What would be best practice to keep css maintainable without losing the module states and without repeating the same css-code to every module-state class?

This is something that I want to address, as you're not the first person to ask me about this.

If you have a JS constructor that was responsible for making an element show/hide then I would consider architecting it as follows:

var collapser1 = new Collapser(el, { cssHideClass: 'moduleA-isHidden' });
var collapser2 = new Collapser(el, { cssHideClass: 'moduleB-isHidden });
Then I might consider this in the CSS using the comma for reuse:

/* hidden */
.moduleA-isHidden,
.moduleB-isHidden {
display: none;
}

This is briefly addressed here: http://maintainablecss.com/chapters/reuse/#what-if-i-really-want-to-reuse-a-style

However, if this becomes painful or should I say unmaintainable then you could consider slightly breaking away from STRICT MaintainableCSS guidelines:

.globalState-isHidden {
     display: none;     
 }
Then not requiring the option for each "collapser" because you can hard code it within the collapser object:

var collapser1 = new Collapser(el1);
var collapser2 = new Collapser(el2);
Whilst this latter one, might at first appear to be more maintainable, and less code, you have to be careful with it. The trade off is that if something is collapseable due to that class but also has other visual difference based on that state, then it's likely that you won't want the exact same visual look for all the modules that rely on "isHidden". Does that make sense?

I need to formalise the approach to this a bit more and it's high up on my list.

HTH for now.

Update: it's also worth noting that this is a bit of a rare case, that might make more sense as a utility class. But as soon as ModuleA or ModuleB has different "isHidden" behaviour I wouldn't attempt to reuse it, and I would tie the functionality to the module in question as per the first approach above.