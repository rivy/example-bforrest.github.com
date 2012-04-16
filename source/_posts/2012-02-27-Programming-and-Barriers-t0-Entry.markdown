---
layout: post
title: Programming & Barriers to Entry
---

A [fellow learner](https://twitter.com/#!/coridrew) has posted ["Programming & Barriers to Entry"](http://truncatedcodr.wordpress.com/2012/01/25/programming-barriers-to-entry/). Cori has much to say in this article concentrated around command line tools, vim and Ruby. I&#8217;d like to comment on some of the perceptions and share my own opinions.

<h3>Command Line</h3>

I picked up on some discord with regard to this type of interaction.

<blockquote>

&#8230;Intellisense (or lack thereof).  Ctrl-spacebar is my friend. It’s what I’ve grown to love. Typing /?—&gt;enter—&gt;up-arrow—&gt;space—&gt;command-I-really-need is a bit of a PITA. It feels like a clunky waste of time.

</blockquote>

Aren&#8217;t these the same type of interaction? CTL+Space pops up a list of available commands, arrow up/down to select and hit enter to paste that text into the window. Granted Intellisense is more polished and will show all of the overloads, but I honestly have a difficult time understanding the difference.

[Git Immersion](http://gitimmersion.com) was very helpful for ramping up quickly with Git. Git is just a plate full of awesome. I can get tons done with four basic commands after I can Alt+Tab to  my bash shell:
```
git checkout -b working_branch #separates my code from the herd.

git status #to see all of the files that I've modified since my last checkin. 

git add . #readies them to be committed to the local repository.

git commit -m &#8216;checkin comment&#8217; #stores them away. 
```
I don't have to right-click anything! Since I'm working locally, I'm not at the mercy of a flaky connection to a central server. When I want to diff files, that happens locally too. 

I've got BeyondCompare set up so in the bach shell I can use 
```
git difftool 
```
and then roll through all of the files that I've changed and it's pretty snappy. 

```
gitk all
```
Shows the entire history of the repository 

```
gitk filename
```
Will do the same for a single file.

There is a git gui as well as  [Tortoise Git](http://code.google.com/p/tortoisegit/) to go along with Caleb's favorite.

<h3>VIM</h3>

It is a very powerful text editor. It really is language agnostic and enables development in a huge variety of languages. Visual Studio, not so much. I started fooling with VIM when I started doing the Ruby Koans. I stumbled through the help tutorial a few times over several months and got the hang of using VIM for navigating documents with the home row keys and pattern matching searches. I try to use it when I&#8217;m not doing .net development, but I&#8217;m still staying in the shallow end of the pool. I&#8217;m still much more comfortable navigating a C# project with Resharper/CodeRush inside VS than I think I&#8217;ll ever be with VIM, but VS has a 10 year head start.

<h3>Ruby and Macs</h3>

There seems to be a strong correlation between Macs and Ruby developers among <a href="http://dallashackclub.com/" target="_blank">Hack Club</a> attendees. Many of the folks who attend do own Macs. <a href="http://improvingenterprises.com/" target="_blank">Improving Enterprises</a>, my employer and sponsor of many wonderful user groups, has an amazing employee purchase plan for computers and many of the consultants take full advantage of that benefit. Several of the Macs at Hack Club are running Windows 7 in native mode and many more are running Windows 7 via VMWare Fusion of Parallels.

I&#8217;d hazard a guess that <a href="ttp://twitter.com/gregvaughn" target="_blank">Greg Vaughn</a> is in the minority and using Ruby in OSX. <a href="http://twitter.com/amirrajan" target="_blank">Amir</a> boots to Windows natively via BootCamp and I believe does all of his Ruby development under Windows. I&#8217;ve installed Ruby 1.9 in my VMWare instance and use Growl For Windows and a ruby command prompt for SpecWatchr when I&#8217;m deliberately practicing BDD through the beauty of <a href="http://www.nspec.org/about" target="_blank">NSpec</a>. Ruby in this group is more about learning something new since most of the crew work in .net for paychecks.
