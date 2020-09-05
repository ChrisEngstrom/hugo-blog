---
title: "Fiddling With Javascript"
date: 2010-06-22T12:00:00-05:00
publishdate: 2010-06-22T12:00:00-05:00
description : "The client wanted to be able to click the actual position title and have the description appear and disappear accordingly."
type: post
author: Chris Engstrom
tags: ["show", "hide", "css", "getElementById", "JavaScript", "PHP", "web development", "WordPress", "T&S Web Design", "old site",]
---

### Intro

While I was at work the other day we received an update request from a client. Since I saw it first I assigned it to myself and started to work at it. There were only two things that the client wanted us to change. The first was changing the suite number for a particular address, which took about five seconds to track down and change. The second was that he wanted to post a job on their careers page. Posting the job was easy enough but he also had another thing he wanted done at the same time. He wanted to be able to click the actual position title and have the description appear and disappear accordingly.

It was towards the end of the day by the time I got to this task so I did a little research and fiddling around with some JavaScript but was unsuccessful in my attempts to get it to work right. So, to try to learn how to do that specific task and learn more about JavaScript in general, I am creating this post. Here goes nothing.

### Importing External JavaScript File

The first thing I am doing is creating a .js (JaScript) file to write my code in. I will be placing it in header.php right after the other .js file that was included in my template. It doesn’t really matter where you put it (body or head) but from what I have read, if you are importing an external .js file it is generally uniform to put it in the head. Here is how the line of code looks.

``` php
    <script type="text/javascript" src="<?php bloginfo('template_directory'); ?>/js/show-hide.js"></script>
```

#### *New Site Note*

Since this site is no longer a WordPress site the setup for the functionality has changed to not include a separate JavaScript file for the function required to show/hide the text and instead it is included directly in this post. Granted, it probably could have been done this way originally but you live and learn. See the end of the post for the [full code example](#full-code-example).

### The Actual JavaScript

The next part required a little bit of research (google) and some programming know how learned from some beginner programming courses that I have taken. I’ll show you the code, then explain it.

``` javascript
    function switch_hidden(id) {
        var e = document.getElementById(id);
        if (e.style.display == 'block')
            e.style.display = 'none';
        else
            e.style.display = 'block';
    }
```

``` javascript
    function switch_hidden(id)
```
Creates a function called switch_hidden that takes the id of an element as its parameter.

``` javascript
    var e = document.getElementById(id);
```

Creates a variable named e and goes to the document and gets the element passed to the function (id) by using just the id that was passed. You now have the element, whatever it is, stored in e.

``` javascript
    if(e.style.display == ‘block’)
        e.style.display = ‘none’;
```

If e’s styled display is set to block, change e’s styled display to none.

``` javascript
    else
        e.style.display = ‘block’;
```

If e’s styled display is not set to block, change it to block.

Something to keep in mind is that we are only going to call this function when a line of text is clicked.

### Implementation

Setting up the html so the JavaScript can work with it is kind of confusing but once you see it it makes sense. At least it did for me. If you don’t mind the text that will trigger the event to show or hide the other text looking like a link then you can skip step one.

1. The first thing you are going to need to do is create a `<div>` around the element that you want to click to trigger the event and give that div a class. I named mine “show-hide”. This step is only useful to make the element not look like a link later using css.
2. Next you should put the type of element that it is going to be. Whether that is a `<p></p>` or, in my case, `<h4></h4>`.
3. Inside that tag make an anchor tag and give it an onclick event of `“switch_hidden(‘#’);”`, then close the opening tag and put in the text you want to be the trigger to show and hide the text. It should look something like this.

    ``` html
        <h4><a onclick=”switch_hidden(‘#’);”>Click Here…</a></h4>
    ```
4. Now create another `<div>` and give it an id that relates to what it is. For my example I will give my div the id of “lorem”. As a note, with the way I have the function set up, to make it work correctly the text should be hidden to begin with so I will also be giving my div a class called “display_none”. In the css I do exactly that with this code.
    ``` css
        .display_none{display:none;}
    ```
5. You can now fill in that `<div>` with whatever content you want to be able to show and hide.
6. Once you are done doing that you need to link that `<div>` to the function we created. To do that all you need to do is pass in the id of the content `<div>` we just made. So in the case of our example you would change point 3.1’s code to…
    ``` html
        <h4><a onclick=”switch_hidden(‘lorem’);”>Click Here…</a></h4>
    ```

### Done

And you should be done. My next heading and paragraph will be the example. Click on the heading and the paragraph underneath it will appear. I hope this helps you a little bit. I tried to be thorough in my explanation so I am sorry if it seems a little lengthy for such a simple function. I did leave some of the css styling out but I will more than likely add that at a later date when I have time.

{{< rawhtml >}}
<script type="text/javascript">
    function switch_hidden(id) {
        var e = document.getElementById(id);
        if (e.style.display == 'block')
            e.style.display = 'none';
        else
            e.style.display = 'block';
    }
</script>
<div class="show-hide">
    <h4>
        <a onclick="switch_hidden('lorem');" style="cursor: pointer;">Click Here…</a>
    </h4>
    <div id="lorem" style="display: none;">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras eros turpis, semper eget convallis eget, vehicula vitae odio. Donec vulputate fermentum urna, ultricies volutpat dolor sagittis et. Nullam id massa vitae sem condimentum tristique et in urna. Curabitur sit amet tellus in nisi viverra pretium eget porttitor magna. Mauris ut mi risus, in volutpat lorem. Aliquam erat volutpat. Aliquam eu consectetur lacus. Fusce mattis dictum mollis. Vivamus feugiat velit a lectus mollis interdum. Proin risus tortor, aliquam ut rutrum ac, accumsan vel quam.</p>
    </div>
</div>
{{< /rawhtml >}}

---

### Full Code Example

``` html
    <script type="text/javascript">
        function switch_hidden(id) {
            var e = document.getElementById(id);
            if (e.style.display == 'block')
                e.style.display = 'none';
            else
                e.style.display = 'block';
        }
    </script>
    <div class="show-hide">
        <h4>
            <a onclick="switch_hidden('lorem');" style="cursor: pointer;">Click Here…</a>
        </h4>
        <div id="lorem" style="display: none;">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras eros turpis, semper eget convallis eget, vehicula vitae odio. Donec vulputate fermentum urna, ultricies volutpat dolor sagittis et. Nullam id massa vitae sem condimentum tristique et in urna. Curabitur sit amet tellus in nisi viverra pretium eget porttitor magna. Mauris ut mi risus, in volutpat lorem. Aliquam erat volutpat. Aliquam eu consectetur lacus. Fusce mattis dictum mollis. Vivamus feugiat velit a lectus mollis interdum. Proin risus tortor, aliquam ut rutrum ac, accumsan vel quam.</p>
        </div>
    </div>
```
