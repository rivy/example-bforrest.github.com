---
layout: post
title: "Fixed Navigation Bar With Twitter Bootstrap"
date: 2012-04-18 15:27
comments: true
categories: [CSS, Twitter Bootstrap] 
---

[Twitter Bootstrap](http://twitter.github.com/bootstrap/index.html) has many very interesting features available. I really liked their fixed sub navigation menus for the feature pages. As you scroll past the subnavigation, it docs with the top of the scroll window and stays there. It also enables click navigation to other feature sections.

I wanted to have the same functionality for my own html pages, so I started digging around. Looking at the page source, I saw an include for "/js/application.js", which is included in the github source project, but is not part of the downloaded assets. At the top of the file is this nice disclaimer:
``` javascript Disclaimer
// NOTICE!! DO NOT USE ANY OF THIS JAVASCRIPT
// IT'S ALL JUST JUNK FOR OUR DOCS!
// ++++++++++++++++++++++++++++++++++++++++++
```
But I discovered that it is not JUST junk, there is a processScroll function that is just what I'm looking for:

``` javascript Scroll function and handler wiring
// fix sub nav on scroll
   var $win = $(window)
      , $nav = $('.subnav')
      , navTop = $('.subnav').length && $('.subnav').offset().top - 40
      , isFixed = 0

   processScroll()

   $win.on('scroll', processScroll)

   function processScroll() {
      var i, scrollTop = $win.scrollTop()
      if (scrollTop >= navTop && !isFixed) {
        isFixed = 1
        $nav.addClass('subnav-fixed')
      } else if (scrollTop <= navTop && isFixed) {
        isFixed = 0
        $nav.removeClass('subnav-fixed')
      }
   }
```
This wires the processScroll() function to the window scroll event and toggles the navigation element based on where it rests relative to the viewport. The idea being to add the 'subnav-fixed' CSS class to keep the element within the viewport.

Attached to the body tag was the first bit of markup that I needed to see:
``` html Page Markup
<body data-spy="scroll" data-target=".subnav" data-offset="50">
```

The navigation div tags contained the rest of the information:
``` html Navigation markup
<div class="subnav">
      <li><a href="#labels">Labels</a></li>
      <li><a href="#badges">Badges</a></li>
</div>
<!-- along with page sections with matching id values -->
<section id="labels">label information</section>
<section id="badges">badge information</section>
```
By annotating the body tag with the data- attribute of "data-spy", identifying sectional elements with id value and including the 
[Scrollspy](http://twitter.github.com/bootstrap/javascript.html#scrollspy) JavaScript plugin, we are able to synchronize the active menu item with the section that is topmost within the viewport.

Now on my // TODO: list is to trick up the blog template to keep it's top navigation bar fixed along the top...
