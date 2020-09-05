---
title: "HTML/CSS Horizontal Menu"
date: 2010-06-27T12:00:00-05:00
publishdate: 2010-06-27T12:00:00-05:00
description : "Many pages that I have seen that are organized pretty well have horizontal menus, so I want to teach myself how to do them and get good at it."
type: post
author: Chris Engstrom
tags: ["HTML", "CSS", "horizontal menu", "web development", "old site",]
---

Many pages that I have seen that are organized pretty well have horizontal menus, so I want to teach myself how to do them and get good at it. My alterior motive to writing this post is that I need one of these to use for a jQuery post I originally planned on doing before this but forgot the css code back at work. So here I am about to do it again but this time understand it better than I did the first time. That and repitition helps us learn right?  Well anyways once I post this you can look forward to a post about using jQuery’s `slideDown()` and `slideUp()` functions to make your menu look pretty awesome.

### Did someone order a menu?

The first thing you’ll need is a menu to mess with. Now if you don’t already have one that a client will be using then here is a simple little menu I made up. I’ll even put it on here so you can grab it if you are following along. I know this is just a single level unordered list, but for making a horizontal menu that is all you need. In a later post I will add another level to make it a drop down menu.

``` html
    <ul>
        <li>Heading 1</li>
        <li>Heading 2</li>
        <li>Heading 3</li>
        <li>Heading 4</li>
        <li>Heading 5</li>
    </ul>
```

{{< rawhtml >}}
<ul>
    <li>Heading 1</li>
    <li>Heading 2</li>
    <li>Heading 3</li>
    <li>Heading 4</li>
    <li>Heading 5</li>
</ul>
{{< /rawhtml >}}

I have added anchors going nowhere and here is what it looks like without any styling whatsoever (other than what is in my installed theme already):

``` html
    <ul>
        <li><a href="#">Heading 1</a></li>
        <li><a href="#">Heading 2</a></li>
        <li><a href="#">Heading 3</a></li>
        <li><a href="#">Heading 4</a></li>
        <li><a href="#">Heading 5</a></li>
    </ul>
```

{{< rawhtml >}}
<ul>
    <li><a href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

As you can see we have a ways to go to make it look like any sort of horizontal menu that we want to use. Here is what we will have when we are done with our styling:

{{< rawhtml >}}
<ul class="horizontal-menu">
    <li><a class="first_menu_item" href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Let's dig in!

I’ll be giving the `<ul>` (unordered list) a `class` to make it easier to work with in our css. I am going to give mine the id of `horizontal-menu`. What we are going to do first is give the list 20px of margin on all sides, 0 padding on all sides, remove the bullets, and give it an overall width to be contained in.

``` css
    .horizontal-menu {
        list-style:none;
        margin: 20px;
        padding:0;
        width:525px
    }
```

{{< rawhtml >}}
<ul class="horizontal-menu-1">
    <li><a href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Make it horizontal

Now we can change the css to make it display horizontally. We will do so by making every `<li>` (list item) display inline right next to each other with the following code:

``` css
    .horizontal-menu {
        display: inline;
    }
```

{{< rawhtml >}}
<ul class="horizontal-menu-2">
    <li><a href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Get rid of the linky-ness and color it

We are going to want to take out the underline effect of the links along with adding some padding to the top and bottom. To make it look a little more presentable I am going to color the background and text so that it goes with the theme I currently have installed (at the time with with the old site). I’m also going to make the text bold to make it a bit easier to read.

``` css
    .horizontal-menu li a {
        text-decoration: none;
        padding: 5px 0;
        width: 100px;
        background: #32522b;
        color: #eee;
        float: left;
        color: #8292A0;
        font-weight: bold;
    }
```

{{< rawhtml >}}
<ul class="horizontal-menu-3">
    <li><a href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Space it out and give it a border

So right now it looks kinda scrunched against the left side and like it is all melded together. To clean that up some I am going to make the text centered within the 100px it has as well as giving the left side of each of them a 1px border that matches the background of my theme. We’ll just need to add that to the existing `.horizontal-menu li a{}` entry in our css.

``` css
    .horizontal-menu li a {
        ...
        text-align: center;
        border-left: 1px solid #121212;
    }
```

{{< rawhtml >}}
<ul class="horizontal-menu-4">
    <li><a href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Remove the left border on the first menu item

Now that we've added a border to each menu item the first one looks a little off, doesn't it? I try to shoot for pixel perfect designs and implementations so that one pixel border is standing out to me. Let's get rid of that by adding a `.first_menu_item` class to the first menu item's anchor that removes the border by setting the border to none and adding `!important` to ensure it is enforced over any previous CSS rules.

``` css
    .first_menu_item {
        border: none !important;
    }
```

``` html
    ...
    <li><a class="first_menu_item" href="#">Heading 1</a></li>
    ...
```

{{< rawhtml >}}
<ul class="horizontal-menu-4">
    <li><a class="first_menu_item" href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Nifty rollover effect

Ahh, doesn't that look better? The final thing I am going to do is give it a rollover effect. To pick the colors that I liked I used the color wizard found [here](http://www.colorsontheweb.com/Color-Tools/Color-Wizard) (since this post is really old that website may not be the best solution [this](https://coolors.co/) is a newer one you could use or just look for a current color scheme generator you like).

``` css
    .horizontal-menu li a:hover {
        background: #92C088;
        color: #252B30
    }
```

{{< rawhtml >}}
<ul class="horizontal-menu">
    <li><a class="first_menu_item" href="#">Heading 1</a></li>
    <li><a href="#">Heading 2</a></li>
    <li><a href="#">Heading 3</a></li>
    <li><a href="#">Heading 4</a></li>
    <li><a href="#">Heading 5</a></li>
</ul>
{{< /rawhtml >}}

### Done!

That’s it! Now you have a pretty neat looking horizontal menu to use. Of course, like I mentioned in the beginning of this post, I am now going to take this base horizontal menu and create a two tier menu with drop down effects using jQuery. Look forward to seeing that post soon!

{{< rawhtml >}}
<style>
    /* HTML/CSS Horizontal Menu Post */
    .horizontal-menu {
        list-style: none;
        margin: 20px 20px 70px !important;
        padding: 0;
        width: 525px
    }
    .horizontal-menu li {
        display: inline;
        position: relative;
    }
    .horizontal-menu li a {
        text-decoration: none;
        padding: 5px 0;
        width: 100px;
        background: #32522b;
        color: #eee;
        float: left;
        color: #8292A0;
        font-weight: bold;
        text-align: center;
        border-left: 1px solid #121212;
    }
    .horizontal-menu li a:hover {
        background: #92C088;
        color: #252B30
    }

    .first_menu_item {
        border: none !important;
    }

    .horizontal-menu-1 {
        list-style: none;
        margin: 20px;
        padding: 0;
        width: 525px
    }

    .horizontal-menu-2 {
        list-style: none;
        margin: 20px;
        padding: 0;
        width: 525px
    }
    .horizontal-menu-2 li {
        display: inline;
    }

    .horizontal-menu-3 {
        list-style: none;
        margin: 20px 20px 70px !important;
        padding: 0;
        width: 525px
    }
    .horizontal-menu-3 li {
        display: inline
    }
    .horizontal-menu-3 li a {
        text-decoration: none;
        padding: 5px 0;
        width: 100px;
        background: #32522b;
        color: #eee;
        float: left;
        color: #8292A0;
        font-weight: bold;
    }

    .horizontal-menu-4 {
        list-style: none;
        margin: 20px 20px 70px !important;
        padding: 0;
        width: 525px
    }
    .horizontal-menu-4 li{
        display: inline
    }
    .horizontal-menu-4 li a{
        text-decoration: none;
        padding: 5px 0;
        width: 100px;
        background: #32522b;
        color: #eee;
        float: left;
        color: #8292A0;
        font-weight: bold;
        text-align: center;
        border-left: 1px solid #121212;
    }
</style>
{{< /rawhtml >}}
