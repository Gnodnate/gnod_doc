---
layout: post
title: Stanfor CS193p note
---
###Class 2
What's the different between exclamation mark and question mark after the vars?
they are same, but exclamation mark means the var will automatical unwrap.

```
@IBOutlet weak var display: UILabel!
@IBOutlet weak var display: UILabel?
```
###Class 3
Same way to instance array and dictionary

```
var opStack = Array<Op>()
var opStack = [Op]()

var knowOps = Dictionary<String, Op>()
var knowOps = [String:Op]()
```

In Swift Array and Dictionary is struct, not class. When passed to argument, they are copied.
Copied isn't copy actually, untill the value has be changed.

###Class 4
