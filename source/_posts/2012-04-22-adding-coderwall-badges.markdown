---
layout: post
title: "Adding CoderWall Badges"
date: 2012-04-22 10:42
comments: true
categories: 
---

I've picked up a few badges via [CoderWall](http://coderwall.com/) and I wanted to include them on the blog with the rest of the information in the right side column.

CoderWall has [instructions](http://coderwall.com/api) under the sub heading "Official blog badge" that detail how to interact with their web api for retrieving badges. My main investigation was how and where to include these snippets within the octopress templates. 

The comments included in the Octopress _config.yml were quite helpful. This was exactly the guidance that I needed.

``` yml excerpt from _config.yml
# list each of the sidebar modules you want to include, in the order you want them to appear.
# To add custom asides, create files in /source/_includes/custom/asides/ and add them to the list like 'custom/asides/custom_aside_name.html'
default_asides: [asides/recent_posts.html, asides/github.html, asides/twitter.html, asides/delicious.html, asides/pinboard.html, asides/googleplus.html, custom/asides/coder_wall.html]
```

So, I was off to the 'custom/asides/' folder to add a 'coder_all.html' file. Inside this file, I pasted the snippet from the CoderWall api page, updating it to use my user id.
<script src="https://gist.github.com/1585413.js?file=coderwall_badge_markup.html"></script>

I ran thru 'rake generate' and 'rake preview' to see my changes in the browser. I was rewarded with absolutely nothing. Sad Panda. So I looked at the Chrome debug console and found the jQuery was not defined.

The internets have taught me to include my script tags near the end of my mark up, I removed the script tag from my aside template. Since Octopress has a footer.html template, I opened that up to include my script tags, ensuring that the jQuery tag was before the CoderWall js file.
``` html script tags
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
<script src="http://coderwall.com/javascripts/jquery.coderwall.js"></script>
```
One more time thru the 'rake generate, rake preview' dance and... TA-DA! At the bottom of the Aside column I now have CoderWall badges.
