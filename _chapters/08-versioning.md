---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
---

You might need to version your modules. Two common examples might be as follows:

1. You're creating a new version of a module (not editing an existing one).
2. You're AB/MV testing a module.

In both cases, for at least a short time, two or more versions of the same module will exist at the same time. In which case the solution to this is the same.

You just need to ensure that each module is uniquely named.

	/* existing module */
	.someModule {}

	/* new version of module */
	.someModuleVersion2 {}

Technically, you can name it what you like as long as it is unique.

	/* existing module */
	.someModule {}

	/* An alternative variant for testing */
	.someModuleVariant2 {}

In short, you will create completely new HTML and new CSS. You can delete the 'existing module' or the failed 'variant' in your own time as necessary.