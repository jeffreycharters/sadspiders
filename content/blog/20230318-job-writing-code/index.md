+++
title = "I got a job writing code!"
date = "2023-03-18T15:03:07-04:00"

description = "Getting a job writing code was less easier than I might have expected. Purple monkey dishwasher."

tags = ["coding", "zestiness",]
+++

If you're reading this, there's a good chance you are learning to code to try to get a job, attract a mate and live happily ever after. Good for you, what a noble pursuit.

This is going to be a bit of a breakdown of how I got from being someone with some basic HTML and CSS knowledge to the hack that I am today, with a superficial knowledge of a hundred other technologies. Strap in.

### Introduction: The *why* of it all.

I don't do things "just because". Ha ha yeah I totally do but maybe not this time.

Let's jump into the story in about 2016 or thereabouts. I had myself a Raspberry Pi model 3B+ and was teaching myself the basics of Linux. I kept coming across people talking about writing scripts in Python, so I decide to try doing that. I stumbled across the website [Automate the Boring Stuff](https://automatetheboringstuff.com/) because I hate boring stuff and spent some time going through that publication from cover to cover. Neat, I can program stuff now! I tried writing a program to automate some of the boring bullshit for my day job and.. ..it doesn't really work.

At work we run Windows computers without Python installed, so I need to strap an entire Python interpreter into an *exe* file and the whole thing just sort of reeks of hackiness. I am not impressed. So I abandon that ship and just keep doing the boring shit the old fashioned way.

### The Webserver

My first attempt at doing programming stuff has taught me that I need to learn more about how the web works. I start working on a website to crowdsource mountain bike trail conditions using Python and the [Flask framework](https://flask.palletsprojects.com/en/2.2.x/) using a great tutorial by [Miguel Grinberg](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). It went well, and I learned more about relational databases (MySQL in this case) and reverse proxies (nginx) and hosted the whole thing on the Raspberry pi. It's sweet! But no one really uses it and in retrospect it could have been done a lot better but that's also a good thing - I've learned a lot since then!

### The Pandemic

My website was sort of crappy and no one used it and I was working full time in an analytical chemistry laboratory and didn't really know where this whole thing was headed.

Then the pandemic hit and the world lost it's collective shit, and fair enough.

I took advantage of this time to create some Python-based scripts to do some web scraping of some work-related websites that never really went anywhere. I was still working in the lab a few days a week because my job was *essential* but with my extra time I came across the [Full Stack Open](https://fullstackopen.com/en/) course through the University of Helsinki. Was I ready to learn *React*? Isn't React for smart people? What the fuck is it, anyway?

I spent a few week and went through the entire course, diligently completing all of the examples and assignments. Look at me, using javascript like a champ to make a webpage that is *reactive*. Being able to launch apps on Netlify was a game-changer for me, I could finally implement a bunch of these websites for my day job to process my instrument data and save myself multiple minutes a day! React rules! Except I don't really like using Redux and there's something about it that rubs me the wrong way.

Also I learned Git at this point. Fuck yeah!

### Enter Svelte

I don't rememeber how I stumbed across [Svelte](https://svelte.dev/), but it seemed like a next-gen version of React where all the hacky shit had been replaced with native support. I set up an app using their website builder called Sapper. It seemed okay, but I was still lost with respect to web development. There's literally a trillion technologies out there. What's [Go](https://go.dev) like?

### Enter Go

For some reason I thought that maybe I was a back-end guy. The internet fucking sucks sometimes, you know? I don't want to serve ads or collect user data or any of this shit. Maybe writing backend code will give me some sort of bigger purpose, maybe I can crunch data that climate scientists use to make the world actually better. This is a theme I struggle with constantly. Very existential but ultimately unanswerable.

I read some sort of introductory book on Go from cover to cover and performed and the exercises. Woo, Go! The best part is using the walrus-operator to assign variables:
```go
number := 42
```
See? Walrus! I'm also fully aware of the difference between a dynamically-typed language and a statically-type language. Neat! I like that while I'm writing Go in VSCode that I've got code autocomplation thanks to the strongly-typed variables, even though there are still a few concepts that elude me (looking at you, *interfaces*).

Okay, great, now I'm a backend guy a little bit.

### Backend is stupid

I quickly have nothing to program on the backend and Go is a bit scary, what with concurrency and pointers and whatnot. Furthermore, [Sveltekit](https://kit.svelte.dev) is a thing now! Neat! I program another couple of little projects using Sveltekit. Holy shit, React is so shitty compared to Sveltekit! I make the decision that I would rather compete for the scarce few Sveltekit jobs rather than ever have to touch React again. I am firmly a Sveltekit guy and as much of a Rich Harris fanboy as you can be at middle-age. Sveltekit is also basically it's own server, so we can just do everything in javascript!

### Learn all of the things

So now what? At this point I've dabbled in literally a fuckton of different languages and frameworks:

- HTML, CSS, SASS, LESS
- Node, Express, Svelte, Sveltekit, React, Redux, Flask
- Bootstrap, Foundation,Tailwind
- Javascript, Python, Go
- Apache, nginx
- MySQL, sqlite, MongoDB, Mongoose, Prisma

I'm sure there are others that I tried for an hour or two and dismissed, but these are all at least things I have basic proficiency with. My favourite stack has become a sqlite database with sveltekit frontend and prisma acting as the go-between.

#### Interlude: My Day-job It Department Hates me. Until they don't.

I'm still working full-time in the lab throughout this whole process, and have offered to moonlight in the IT department and also have learned a ton of SQL in an effort to become the new database administrator to no avail. Boo. Annoyed.

However, a friend that works in the department vouched for me as a reasonably-competent developer, and I get a one-year contract to develop an in-house e-commerce-type site. Woohoo, coding for a living, suck it everyone!

The project ends up being a success, I am able to ship the projects thanks to the batteries-included [Django](https://www.djangoproject.com/) project. In the end I think the whole thing is a bit hacky, but it has been used in production for nine months at the time I am writing this with no major crap-ups so I'm calling that a win! This was a nice little opportunity that I am happy to have on my resume. Networking ftw! Except I still hate LinkedIn and pretty sure I always will. But if you like it and it works for you, power to you.

### Typescript, btw

As I'm getting deep into the workings of Sveltekit, I am noticing that for some reason they are all about Typescript. I assume, naturally, that I am too stupid to understand Typescript but decide to have a go at it. I dabbled a bit during the Full Stack Open course and was definitely less-than-impressed.

So I read the entire [Programming Tpyescript](https://www.oreilly.com/library/view/programming-typescript/9781492037644/) book and skimmed the parts that were over my head.

I spun up a new Sveltekit project to much around with. It's a bit of a learning curve for sure and I spend a fair amount of time going through the Sveltekit docs to figure out what sort of types need to be assigned to some default variables, but nothing too crazy.

And it turns out, Typescript is fucking awesome. I had heard that it was too much overhead for small projects, but the amount of time I was saving thanks to my IDE's autocompletion is super-great. Getting screwed by inappropriate return types in my functions screwed me a couple of times during my Django project, so I appreciate knowing exactly what each variable looks like and what sort of parameters it might have available instead of `console.log`ging things until they work. I still do that, but just less now.

### Going for the win

At this point I am back in the lab and want to find a full-time remote gig. I've got my stack of choice:

- Sveltekit + Typescript
- PostgreSQL database
- [Prisma](https://prisma.io) ORM
- Maybe some Go because I still like Go even though it's not Rust btw

In order to be able to tell prospective employers that I've got collaborative experience using Git, I create the [STaTioN](https://github.com/jeffreycharters/station) repository. It consists of the very basic building blocks of a modern website:

- `index.html`
- `style.css`
- `script.js`

I initiate those files with a very basic amount of data and ask some of my Twitter friends to get involved if they so choose. They do! It's kind of awesome learning how to deal with Pull Requests and issues and all that type of stuff with no real "Prod" to break, and if you do no one really cares because it's all just there to break anyway. Thanks for getting involved, everyone! I've let the site stagnate, I sometimes think about torching it all back down to the very basics and starting over. We'll see, maybe?

### Finally a job

I applied to many, many places. However, I was also deliberate with my applications. I don't believe in the "spray 'n' pray" school of thought. My cover letters were all tailored to the individual position. I got a couple of interviews, which was promising, and also a lot of radio-silence, which was not. So I just kept applying. I found jobs via the usual job sites, I looked for local developers and contacted them directly.

My break into the field came from a job ad on the Svelte Discord server's job section. Sveltekit had reached the **Verion 1.0** milestone which means "yeah use this in production now, I don't give a shit" which I think gave more employers the confidence to deploy their Sveltekit projects. The company promised resume-free hiring, which is super awesome because resumes are stupid and no one really knows if they're doing them right and the whole thing can just use an overhaul.

So I went through their process, did an online interview, and they got in touch a week or so later with a job offer! Woooo work-from-home FTW!

ᄽ(ノ◕⌢◕)ᄽノ ︵ ┻━┻

**Edit:** The new employer's backend is written in Go and is actually a GraphQL server. So I actually get to write Go professionally! Nice.

### Postamble

![The fat nerdy computer guy from South Park and he's got some mountain dew](computer-guy.jpg)

So that's it. I spent a number of years during my evenings and weekends teaching myself to write code and now I have a job where I sit at home all day and write code. I'm not going to get fat though since I enjoy endurance cycling and regular mountain biking and rock climbing and all sort of other shit.

### My Advice

Did you read this fucking thing? You don't want my advice.

But if you insist, pick some shit you like and start writing code. Keep up to date with things, the field changes every 3 or 4 days and you need to learn a new language or framework or some other shit. Give up and become an electrician or plumber or something. But I guess in the end I'm proof that you can get started on a career as a programmer for basically no monies as long as you have unlimited time to spend learning all this shit.

I do like it though, really.