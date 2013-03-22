---
layout: guide
title: Troubleshooting Common Problems
category: how
description: An overview of the most common email layout problems and how to fix them.
---

# Fonts

----

### iOS creates blue links over dates and addresses

By default some clients (esp. Apple) will automatically turn anything that appears to be a date, phone number, address or URL into a link, in the web's default blue - probably not in your brand's palette.

To do that, add a class in the parent or wrapper of the content and define it with your colors, for example:

    span[class="ios-link"] a {
      color: #117692;
      text-decoration: underline;
    }
{: .language-css}

Source: [Litmus: Banning Blue Links on iOS Devices](https://litmus.com/blog/remove-blue-links-ios)

----

### My text is green in Hotmail!

You're probably using a header tag `<h1>`{: .language-markup}, `<h2>`{: .language-markup}, `<h3>`{: .language-markup}, etc.

I also recommend avoiding `<p>`{: .language-markup} and just do all your font styling inline with `<div>`{: .language-markup}s and using `<br><br>`{: .language-markup} for breaks.

See [general coding tips]({{ site.baseurl }}{% post_url 2013-01-03-coding-style %}) for more detail.

----

### Gmail shows purple, I didn't use Times New Roman…

Where did you define your font styles? You might have distrupted it and forgotten to declare it again. For example:

    <table>
        <tr>
            <td style="font-size:14px; font-family: Helvetica, sans-serif; color: #333;">

            The text will be in Helvetica
            <br>

            <div style="border-top: 1px solid #ccc">
              This text may be unformatted, resulting in Times New Roman or purple text (in Gmail).
            </div>

            This text might also be unformatted or purple.

            </td>
        </tr>
    </table>
{: .language-markup}

To fix this, re-declare your font styles again within your `<div>`{: .language-markup} like this:

    <div style="border-top: 1px solid #ccc; font-size:14px; font-family: Helvetica, sans-serif; color: #333;">
{: .language-markup}

In my daily work, I try to use variables, for example (liquid, twig):

    <div style="border-top: 1px solid #ccc; {{ "{{ basefont " }}}}">
{: .language-markup}

This is different from CSS inline tools for emails which tend to replace your classes with inline styles. Here I'm appending it to other inline styles.

----

### My images and text are running into each other

You are not aligning or floating *and* clearing probably. We frontend developers are generally very familiar with the `.clearfix`{: .language-css} hack. Have you ever looked at how it works? Yes, that's correct, it uses `<table>`{: .language-markup}s!

In normal HTML, you might have something like this:

    <div class="clearfix">
      <div class="i-am-floated-left">…</div>
      <img class="i-am-floated-right" src="kitten.jpg">
    </div>
{: .language-markup}

To help with imagining what non-cleared content looks like, here is a real example of floats *not working*:

![Example from UX Munich Newsletter]({{ site.baseurl }}/images/examples/uxmunich-clearing-floats.png "Example from UX Munich Newsletter")

This example is from a draft of the [UX Munich](http://uxmunich.com/) newsletter. The images are taller than the height of the table cell and bleed into the next speaker's row.

To fix this, all you have to do is wrap each row in a `<table>`.

    <table>
      <tr>
        <td>
          Some content here.
          <img src="speaker.jpg" align="right">
        </td>
      </tr>
    </table>
{: .language-markup}

N.B. The code above is stripped of any superfluous styling markup for readability.

----

### Yahoo shows mobile version

Probably because you're not using attribute selectors. See [general coding tips]({{ site.baseurl }}{% post_url 2013-01-03-coding-style %}) for more detail.
