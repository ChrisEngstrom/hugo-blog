---
title: "Why Isnt This Working?!?!"
date: 2010-10-24T12:00:00-05:00
publishdate: 2010-10-24T12:00:00-05:00
description : "When working with JavaScript or jQuery it is important to remember to check and make sure that the basic functionality is working correctly before you get frustrated and upset that absolutely NOTHING is working."
type: post
image: images/blog/why-isnt-this-working/jQueryAlert.png
author: Chris Engstrom
tags: ["alert", "inspect", "JavaScript", "jQuery", "web development", "old site"]
---

When working with JavaScript or jQuery it is important to remember to check and make sure that the basic functionality is working correctly before you get frustrated and upset that absolutely NOTHING is working.

Recently I was working on a project at work and no matter what I did with my jQuery statements, I couldn’t get anything to work. I was looking at examples online and making sure mine was following the same concept but still nothing was working.

I decided to skip that part and just keep moving so that I could come back to that problem with a clear head later on. As I was working on other things I noticed that whenever I inspected an element (using Chrome’s built in feature) I had a JavaScript error. I wanted to figure out what it was since at that point I didn’t have anything really doing anything in my jQuery section. So I put in a simple alert call to see if it would display:

``` javascript
    alert("Your JavaScript/jQuery is working fine! :-D");
```

Which of course that didn’t show up. I started looking real hard at the code only to find that one of my functions wasn’t closed correctly and wasn’t throwing an error in NetBeans for some reason. I fixed that problem and the alert displayed fine after that so I knew my jQuery would work now. Hurray!

The moral of this story is to always test your JavaScript/jQuery with a simple alert to make sure it is working before you spend minutes, or even hours, becoming frustrated that nothing is working correctly. And yes, I feel really dumb for feeling the need to post this but I figure it might help someone else or at least make them laugh a little 🙂
