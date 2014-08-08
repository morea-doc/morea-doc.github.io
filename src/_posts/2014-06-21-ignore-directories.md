---
layout: post
title:  "Ignore directories"
date:   2014-06-21 14:29:39
---

The latest version of basic-template contains an update to the MoreaGenerator.rb file which now ignores any directories inside the `morea/` directory named `_ignore`.  This allows you to store private data inside the `morea/` directory if you (for example) which to associate tests or other files with the module.

For more details, see the [private data section of the user guide](/userguide.html#Addprivatedata).

To obtain this update, run the `morea-merge-upstream.sh` script.