+++
title = "Lesson: make other people's lives easier"
date = "2023-06-30T08:40:07-04:00"
draft = false
#
# description is optional
#
description = "or Don't make me do extra work."

tags = ["coding", "zestiness"]
+++

### Don't make me do extra work

I've spent a lot of years in school. Of those years, four were spent as an undergraduate student. Another ~four were spent as a graduate student. As stupid as those terms are, they let me see life from two different perspectives.

On the one hand, undergrads are stupid idiots who exist to annoy professors and graduate students with their stupidness. Graduate students exist to do the grunt work for professors and annoy postdocs with their stupidness. Part of that grunt work is to mark undergrad papers and assignments so that the professors don't have to. This is what I'll be focusing on today.

While an undergraduate, we would chat with the graduate students who would babysit us while doing lab sessions. They hated marking because it's boring and undergrads are stupid. And I realized that since they are human, making their lives easier would like correspond to a better grade. And I think this worked. My work was always well-researched and I put a lot of effort into it. But I would also keep things short and to the point and not wax philosophic about unrelated bullshit.

### Don't make *me* do extra work

Being the type who sometimes makes poor life choices, I eventually became a grad student myself. Indeed, marking papers blows. How did you get to third year and still do *x*, *y*, and/or *z* so wrong? And I could always tell the people who knew their shit because it was succinct, it was to the point, and it was *clear*. If people write an extra 1200 words trying to eke out an extra point or two, you're making me do extra work and now I'm grumpy and sinceI am human, will probably give you a slightly lower grade because I'm not convinced you know what you're doing.

### Transferrable skill

Fast-forward a few years to today. I've got a job as a web developer! I am super smart and can write *declarative* code! My code does what it is supposed to! I am really good at this!

> \*submits PR for review \*
>
> **senior dev (to self):** this is a fucking nightmare
>
> **senior dev:** this is a fucking nightmare

Wait, what? I am so smrt.

![stupid spongebob meme - text says enjoy my giga-pr](giguh-pr.jpg)

I fell prey to one of the classic blunders. I tried to make them do extra work.

Don't make other people do extra work.

### Keep it simple, stupid

Going back through my `diff`, there were a ton of things in there that didn't need to be there. I didn't do as little as possible, and nothing more.

So if you're a junior dev, or looking to get into the field, go through your diff, you can see everything in the `changed files` section of your PR on github.

Look for stuff like this:

```diff
- 
+ console.log("test")
+ unusedValue = "works?"
```

Spend the time to get rid of your goofy shit that doesn't work. We all do it, but the trick is to pretend you don't.

Or stuff like this:

```diff
- id
- address {
-    id
-    name    
-}
+ cats
+ id
+ dogs
+ address {
+    id
+    name
+}
```

Sometimes you'll need to structure your data like that for clarity or readability and that's totally fine. But you could probably go back and shuffle things around so that the diff just ends up like so:

```diff
id
+ cats
+ dogs
address {
    ...
}
```

This seems a lot easier to read for the person who will be reviewing your code.

While perusing your diff, it's also a good time to assess your functions and variable names and make sure that you're happy with your code and that you won't come back in a month and ask yourself "what [eff word]ing idiot wrote this?!" before finding that the blame points squarely at you. Try to write code you are proud of.

And if by doing this you also make less work for your coworkers, all the better.

### I think, at least

Look, I'm a few months into a junior dev role. This seems to make sense to me. There's a quote [attributed to Einstein](https://quoteinvestigator.com/2011/05/13/einstein-simple/) whic states:

> Everything should be made as simple as possible, but not simpler.

and I feel like this is a good application of that.

Can any more experienced devs weigh in? Shout me out, I'm [@lowpivot](https://twitter.com/lowpivot) and I'd really appreciate some feedback. I know this is by no means a deep dive, but I feel like this is an important lesson to learn as a junior.

Anything else that might seems simple and intuitive but often overlooked by the rookie on the team? Let me know! Thanks, hope this helps somebody.
