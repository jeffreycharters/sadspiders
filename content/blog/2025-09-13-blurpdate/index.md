---
title: "Blurpdate: some new lipstick on Blurt"
slug: "blurt-2"
date: "2025-09-13T08:42:12-04:00"
description: "Blurt was shitty but now it's a little more or less shitty depending on how you feel about nonsense."
tags: ["education","zestiness","coding"]
---

 🎵 Now playing: *Caspian - Hymn for the Greatest Generation*

For those who aren't familiar, [Blurt](https://blurt.sadspiders.ca) is the only web project I've actually left functional for any period of time while maintaining any sort of interest in. For all intensive purposes it is a joke. It is twitter capped at 14 characters so there's no way you can communicated anything but nonsense. There is no account security, so you can use your enemy's username and post caring, loving things as them. The possibilities are ~~endless~~ stupid!

I just wanted to write a post on the changes that were made. Not because anyone cares. But because I have been off on holidays for a week and what the hell else am I going to do?

### What you can't see

#### Shitty server stuff

The way I had blurt set up initially was pretty stupid. At the very start, when I made Blurt in a few hours to entertain some friends during the Pandemic and I wrote the whole thing in javascript using a framework called [Sveltekit](https://svelte.dev). It worked! Sveltekit in a nutshell is a way to make "web apps" which is like a web page but with more interactive stuff. When you sent a blurt you would see it immediately on your screen, and in the background it would check every ten seconds if anyone else had sent anything new, and if they had it would update on your screen as well.

But I wanted chaos! What if I am sending out a BlurtStorm™ and someone else is also sending out a BlurtStorm™? I want all that shit to be raining down on everyone's screens in real time. To do that, checking every ten seconds wasn't good enough, I wanted as intantaneous as possible.

Tbere's a technology that can do this called WebSockets. They basically keep an open connection to the server and receive updates immediately! Unfortunately, Sveltekit doesn't play nicely with websockets.

So because I am a nerd and wanted an excuse to do so, I started writing a new webserver in a language called [Go](https://go.dev) that plays nicely with websockets. So now I've got two web servers! When you would visit the website, you'd get most of the stuff from the Sveltekit server. It would then open a connection to the server written in Go to get the Blurts.

So now I have to make sure both servers are up and functional and that when Sveltekit wants to talk to Go that things are going through the correct routes. Ach, it is too much!

Oh and also the fucknut I was working for at the time liked to use a thing to talk with the database that sorta works but was super overkill for what I was using it for. So I wanted to scrap that too.

#### Rewrite it all

So I scrapped the whole Go part, and had a plan to rewrite it in go. *Because*, at some point I had the brilliant realization that I would be able to build the Sveltekit part, package it up into a nice little package, and [actually build it into the Go server](../go-echo-sveltekit). I wrote a blog post on how to do this, since what I found online seemed a bit lacking in the how-to department.

So now while I am working on this stuff I have to run the two individual servers, but when I go to run the whole thing, I can pack it down to one and it still works real nice. Which means only one server to make sure is working and no fancy setups to redirect things various places, which is a win.

I also started using a library to talk to the database called [Jet](https://github.com/go-jet/jet) which made that part of things a lot nicer to deal with.

### The stuff you can see

#### Instant updates

Websockets still work and so now when you have people having Category 3 BlurtStorms™ everything will be delivered to your screen as quick as can be! Live Blurting is so much more meaningful now. So that's good. No degradation of expectations.

#### Personas

One of the best things about Blurt is that there is no account security. Anyone can Blurt as any username so long as it contains 14 or fewer characters. This makes my job a lot easier since I don't have to give a shit about security, and it offers the users plausible deniability about the super-inappropriate things they are Blurting.

So now you can set up a roster of usernames to Blurt as, which I call personas. You can have a stable of up to 20 personae to Blurt as. All alone on Blurt? No problems, have a conversation with your many selves!

#### Chaos

I have also introduced Chaos Mode™ as an extra layer of fun to personae. In the persona manager drawer™, there's a toggle to engage Chaos Mode™. If you activate this, Blurt will chance to a random persona after each Blurt you send! This is truly random so don't necessarily expect it to change after every Blurt. So now you can Shout over yourself or be optimistic and motivational as a whole youth group at once! Or whatever!


### What does the future hold?

No one can predict the future, least of all Technical Supervisor's of Veterinary Toxicology laboratories. However I do plan to introduce Stables™ sometime in the near future. A Stable™ will be a saved set of Personas that you can load up at will instead of having to load up all of your Personas one at a time if you are stuck on a new computer in the library or something. They will be saved the same as everything else in Blurt, so give yours a unique name or some asshole is going to come along and fuck with your Stable ugh this is why we can't have nice things and end up with Blurt.


### Conclusions

Blurt has been a fun distraction for me and I am a bit disappointed to be coming to the end of this chapter. I know Blurt is dumb as hell, but I think it at least isn't actively harmful like most things on the internet and it is a *very jeffrey* thing in its uselessness but also having an inordinate amount of thought go into it.

So go [Blurt](https://blurt.sadspiders.ca). Enjoy what an IQ of 96 and a bunch of spare time can get done.