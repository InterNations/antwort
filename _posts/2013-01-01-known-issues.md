---
layout: guide
title: Known issues
category: how
description: Known issues with Antwort and workarounds.
---

# Known issues

---

### 1. Sparrow for iOS - responsive columns don't work

*Reported and solution by [@dandenney](https://twitter.com/dandenney)*

In Sparrow for iOS, the columns don't properly transform into rows (see screenshot below). Dan reported that the `display: block` applied to `<td>` doesn't work in Sparrow. To get around this he [added another set of nested tables](https://twitter.com/dandenney/status/312295707874824192).

Because Sparrow is no longer in development and (as far as I know) not a major Email client on iOS, I've decided to leave the Antwort template as is but post Dan's solution here.

![Columns in Sparrow for iOS]({{ site.baseurl }}/images/guide/sparrow-ios-columns.png "Columns in Sparrow for iOS")

*Columns not working in Sparrow on iOS*

----

**Found an issue?** [Let us know](https://github.com/InterNations/antwort/issues).
