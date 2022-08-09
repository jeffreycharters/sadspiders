+++
title = "New Project: DH Bike Plates"
date = "2022-08-01T08:30:30-04:00"
description = "Let's make our backend look good, a project to help myself"
tags = ["coding", "dh racing"]
draft = false
+++


### Introduction - Problem Description

As everyone who knows me knows, it is not often that you can get through a conversation with me without having bikes come up.

And since I am a lot lazier than people like to think, I would rather watch biking than participate. So every year I make sure to follow the [UCI Downhill Mountain Bike World Cup](https://www.uci.org/calendar/mtb/1voMyukVGR4iZMhMlDfRv0?discipline=MTB) (*Union Cycliste Internationale*) and watch all of the races lives where possible.

During the run-up to each event, a number of media outlets provide video of practice runs to get an idea of what the track is looking like and how various riders are tackling the difficult sections of track. Althought I very much appreciate what they do, it irks me a bit that they don't include each rider's name on screen to know whom's who. Further complicating things, the plate number for each rider changes *every single stupid race*, which means you can't even just memorize plate  numbers.

### My solution

Since the plate number is based on the riders' current UCI ranking, I'm going to take the information from UCI's website and add it to a database using [Planetscale](https://planetscale.com) and their generous free tier to see hwow things go. I want to add Prisma as on ORM because I like using Prisma as an ORM. I'll start out by simply creating a backend API using TypeScript and [Express](http://expressjs.com). It will start out being **really** bare-bones, since I want this up and running by mid-week in it's most basic form.

Once I have the backend up, I will write a *very* simple front-end, probably using Svelte (and Tailwind for prettification) to consume the API. Since this is going to be primarily a mobile app so I can use it while plopped in front of the TV, I have grand plans of using a touch-based quick-scroll mechanism, I'll see how easy that will be to implement.

Short term, I may just have to print the information on-screen and have a font-size adjuster so we can get the information as quickly available as possible. This is required because there is no real pattern in the footage being shown in these videos -- you may need to jump from plate 35 of the Elite Women to plate 87 for Elite Men to plate 1 of the Junior Men, so an intuitive interface will be required.

### Downsides

I really want to write a project using Test-Driven Development (TDD). Unfortunately, I want this done *fast* rather than *well* so it won't happen right yet. However, I may continue this project into the winter which could allow for TDD of future functionality. My time limit and "would rather have it work than work well" attitude wil preclude *any* unit testing during the initial roll-out.

### Requirements

- [ ] set up dummy data
- [ ] set up basic API with Express
- [ ] set up Planetscale DB
- [ ] write Prisma schema and sync with DB
- [ ] verify API works as expected
- [x] make entire front-end first?!


## Deadline

There is a race this week, meaning footage should start rolling out in about two or three days. I want to have *something* in place and working by then. Even if it's just a big list of all the riders.

**Best case:**
{{< img src="best-case.jpg" alt="Stylish rider jumping between two trees" >}}

**Worst case:**
{{< img src="worst-case.jpg" alt="Stylish rider jumping between two trees" alt="Rider on their back after a crash with their bike airborne beside them">}}

On the flipside, there's a race next weekend! I encourage everyone to get on board, it's exciting to watch!!

