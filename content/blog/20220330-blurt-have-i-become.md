+++
date = 2022-03-31T23:13:00Z
description = "What the shit even is TypeScript? What the shit is even real, you know?"
draft = true
tags = ["coding", "zestiness"]
title = "Blurt Have I Become?"

+++
### A blurt-eat-blurt world

Everything truly great starts as a joke. Religion, capitalism, the movie Idiocracy. But then it rallies some support and just look where that's gotten us.

My current highest-grossing side-project is called [Blurt](https://letsblurt.duckdns.org) (tied with all the others at $0). During a video by a youtube guy [Tom Scott](https://www.youtube.com/watch?v=NYj3DnI81AQ), was going through some of his own historic predictions of what now would look like. He thought that blogging was going to remain big, which didn't happen and was somewhat usurped by social media and _tweets_.

Being a little bit _on the spectrum_ (probably), my brain continued the obvious trend: the future of tweets is bleak, and people will desire to communicate with even harsher character limits.

### Enter Blurt

My idea for project was to create the **world's first micro-tweeting platform called Blurt** (stylized **BLURT** because onomatopoeia). You can write whatever you want, so long as it consists of 14 characters or less. But greater than 0 characters. It may not be the first, I didn't do any market research in case I am wrong and can't say that.

It already exists and it is great. In case you haven't tried it yet, [here is a link to Blurt](https://letsblurt.duckdns.org). I'm also proud of the fact that I didn't feel like dealing with login and user authentication and shit like that so I just didn't bother with it. That's right, you can impersonate others or log in as like twelve different users simultaneously. Or the same user twelve times. At this point I'm lucky no bots have discovered it, but also maybe bots are excited they haven't discovered it because how much spam can you spam into 14 characters?

### The crowning achievement

Everyone on blurt has that stupid "verified" checkmark after their name because we are an open and inclusive mess.

### And yet..

There are a few other features I want to add to blurt. I want to add infinite scroll, so that when you're about to get to the end of the blurts, another batch load up. I want to have a "currently online" count, and be able to break that down into "socs" (pronounced like soashes, short for socials) and "jerks" where soashes are the cool people who post (go read [The Outsiders](https://en.wikipedia.org/wiki/The_Outsiders_(novel)) or it won't make sense and that's on you) and jerks just lurk and don't add to the cacaphony. You can't spell cacaphony without caca unless you spell it correctly!

Also I need to make it more friendly to desktop users, since I made it originally with mobile in mind but I feel like it would be a fun thing to have up in a window behind all the work stuff I'm pretending to do.

So if I'm going to do all this shit anyway, it turns out I'll probably just start building it from the ground up again. Which isn't nearly as daunting a task as I'm pretending it is since in its current state, Blurt literally took me two days to throw together, and also I wrote a bunch of other code for my daytime job during those two days.

### Quels seront les changements?

The site was originally an excuse to try to make something using an emerging web technology called [SvelteKit](https://kit.svelte.dev/). I enjoyed monkeying with SvelteKit, but quickly learned that it was massively overpowered for my use-case. It's more for making a full-fledged website, whereas Blurt could easily be accomplished using what us big nerds call a SPA, or a single-page application. It will seem like you are at the login page and then on the chatting page, but really they are the same page and the code just makes it look like there is a new URL, even though in reality you're still on the same page but like, with a different background. Weird, eh? You probably use this type of stuff all the time without realizing it.

So SvelteKit is going to get put on the backburner, and will be supplanted with a FRONT-END which the user interacts with, and a BACK-END which is where the database lives and where all the big decisions are made (aka the business logic).

#### Front-End Stuff

The front end stuff will be written in [Svelte](https://svelte.dev/) which is similar to SvelteKit but better for dealing with purely user-interface stuff. Anything the user deals with is user interface. So yay, you'll get to see the end result of something written in Svelte! Also to make the page pretty I like to use a project called [TailwindCSS](https://tailwindcss.com/) because I don't like using an extra file to tell the browser how to make everything look, which I've always begrudgingly accepted. But now everyone else has also decided we hate doing that so now we can stop!

#### Back-End Stuff

Feel free to skip this part, but I am more excited about this than the front-end stuff. I'm trying to write for a general-audience instead of just dweeby code-nerds, so hopefully it makes some sense and may even offer you a window into wtf happens behind the curtain on websites.

Right now when Blurt loads the page containing blurts, it loads 250 of them. Then two seconds later, it checks again and downloads them again if they haven't changed. If there has been a change, such as a new Blurt, it.. ..just downloads them again. Every two seconds. Forever. The browser makes a _request_ to my server, and the server sends the _response_ to the request. It's a process called polling and it works fine for this purpose but it isn't very elegant and I don't love it.

I want to make use of a technology called websockets. Intead of the request/response cycle, the browser and server make a connection and the connection is maintained between them. That way, instead of the constant request-response cycle, the server can just send a new blurt whenever someone else posts one! This wasn't possible the way SvelteKit works, so I need to create a new server that will happily do websockets stuff.

To write the new server, I will use a language called TypeScript. Most people have heard of Javascript, and it works great in a lot of cases. But there is a concept in computers called "typing". *types some words*. No but for real. Here's the basic idea: the letter "c" is a character. That's a type. The word "cat" is a string \[of characters\]. Strings are types too. There are lots of others and users will usually need to create custom types. In javascript I might write some code that sends a string somewhere else. But what if that code is only expecting a character and a string causes it to break? I'm boned! TypeScript is designed to make it so that can't happen. If you write the code that sends a string to somewhere that is expecting a character, TypeScript will give you a stern look and a shaking head while pointing out the error of your ways. It's like a safety net for people like me (and everyone else) who write sort-of pretty shitty code.

### The nutshell

In broad strokes, that's it. Well, not totally. My database is almost as basic as possible, a little guy called sqlite (pronounced like "sequel-light"). It gets the job done for the like five users a day I get. To talk between the code and the database I have a little helper called [prisma](https://prisma.io) which I actually like more than I should for some reason.

When will this happen? I don't entirely know. In my defense, I can't really remember how to program a server like this, I haven't really done it in a year or so. But luckily there's a million youtube videos to steer me in the right direction. And I've never used TypeScript in a project before. I figure that to land a job, having a bit of experience with it will be looked at with a sly, knowing grin. Having said that, there's no time like the present, so let's say I start tomorrow night and try to have something together by the end of April? That's a month. If the weather is good I might not do much, but I'll try to put in some honest effort. mmmmkay?