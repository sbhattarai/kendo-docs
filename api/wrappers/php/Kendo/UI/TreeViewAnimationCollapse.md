---
title: TreeViewAnimationCollapse
slug: php-ui-treeviewanimationcollapse
tags: api, php
publish: true
---

# \Kendo\UI\TreeViewAnimationCollapse

A PHP class representing the collapse setting of TreeViewAnimation.


## Methods

### duration
The number of milliseconds used for the animation when a node is expanded.

#### Returns
`\Kendo\UI\TreeViewAnimationCollapse`

#### Parameters

##### $value `float`



#### Example 
    $collapse = new \Kendo\UI\TreeViewAnimationCollapse();
    $collapse->duration(1);

### effects
A whitespace-delimited string of animation effects that are utilized when a TreeView node
is collapsed. Options include "fadeOut".

#### Returns
`\Kendo\UI\TreeViewAnimationCollapse`

#### Parameters

##### $value `string`



#### Example 
    $collapse = new \Kendo\UI\TreeViewAnimationCollapse();
    $collapse->effects('value');
