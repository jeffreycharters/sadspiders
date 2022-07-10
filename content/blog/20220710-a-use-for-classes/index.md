+++
title = "Javascript: A Use for Classes!"
date = "2022-07-10T08:30:30-04:00"
description = "I've long been confused on when to use classes in javascript. I found a use-case in the wild!"
tags = ["coding"]
+++

### Build in Public

  I recently mentioned on the [Self-taught Tech Network](https://discord.com/channels/932253730605252609)'s Discord server that I was confused on when to use classes when programming. The server's administrator and probably-not-a-psychpath (Joel)[https://twitter.com/TechPickleJoel] chimed in the remind me with the principle I needed to be reminded of:

  > It's know [sic] as separation of concerns.

  **Editor's note:** Please don't judge him by his typo, he had no idea it would be published for millions to see.

  And with that, the pins started falling into place in my understand of when to use classes.

### Enter domesticity

  Every month or so, my sig oth and I make a pile of receipts and figure out whom owes who how much money over the course of the month. So I dutifully open google sheets and enter some values into some columns and life moves another step forward.

  As you may be aware, I am trying to forcefully shove my career direction into the web development direction. And since it's fun to spend several weekends and evenings to make a web app to save myself five minutes worth of work a month, I'm going to develop an app!

  ![A screen grab from Rick and Morty. The character named Glootie has a tattoo on his forehead which reads "Do not develop my app"](./glootie.png)


### Class is in session 😎

  While trying to determine the bits and bobs that would be required for this app I realized something: a month can be a class!

  There will be a number of components to a month, and I think everything would be easier if I abstracted a lot of logic into its own file. Some examples should help here.

  #### The original idea

  Initially, I had considered making the month as a dictionary, like so:

  ```typescript
  let bills = {
    month: "June",
    people: ["j", "o"],
    recurring: [
      {
        name: "electric",
        amount: 25.34
        }
    ],
    receipts: [
      {
        location: "GroceryCo",
        date: 1657457787,
        amount: 123.45,
        comment: "ignore bike parts for me"
      }
    ]
  }
  ```

  Nothing too complicated here. It's got the month, the people involed, and lists of monthly bills and the receipts we have lying around. But if I were to put my logic in with the rest of my code, this could get ugly in a hurry. For instance, if I decide I want to see the receipts in chronological order, I need to create a new function:

  ```typescript
  // this could be made a one-liner, but for clarity...
  const receiptsChrono = (receipts) => {
    list.sort((a, b) => (a.date > b.date) ? 1 : -1);
  }
  ```

  This is fine, but to use it in multiple places I will need to place it into it's own file and import it wherever it is needed. So if I create a file which exports this function, it will need to be imported as follows:

  ```typescript
  import { receiptsChrono } from './some/dir/receiptUtils.ts';
  ```

  If I add more functions, I could export them all from the `receiptUtils.ts` file at the same time, which would make life easier, but this is still not ideal because I will have a dictionary of the months, but all of the functions to manipulate them will be in a different file. For example:

  ```typescript
  import receiptUtils from './some/dir/receiptUtils.ts';

  bills = {
    // ..see bills dictionary in above example
  }

  sortedBills = receiptUtils.receiptsChorono(bills.receipts);
  console.log(sortedBills);
  // output: list of bills sorted chronologically
  ```


#### Now let's do it with classes

  But let's make life easier on me, since that's the whole point of computers until they rise up and either kill us all or get solar-flared into oblivion.

  Instead of a dictionary, my month of bills is going to be a class I will call Month, since it is a month of bills. I am doing this in typescript, so if something looks weird to you you can probably safely ignore it.

  ```typescript
  // month.ts
  export class Month {
    month: string;

    constructor(month: string) {
      this.month = month
    }
  } 
  ```

  This is the very start of my class, since it is still a work in progress. Hopefully I write more once the project is further along, so stay tuned or sign up to the [RSS Feed](/index.xml) to get it delivered to your feed-reader like a good nerd.

  **BUT**

  Here's how this is going to work. First, I will import and create an instance of this class:

  ```typescript
  let month = new Month("june");
  console.log(month.month);
  // output: "june"
  ```

  So that's great. I'm planning to write some setters, setters and methods in order to manipulate the object that has been made using this class. This will help to *encapsulate* the logic, rather than have it spread out all over the place. The example above was used to create a variable that stored the chronologically-sorted receipts which would then be logged. But using a class, this logic can easily be accessed with less verbosity:

  ```typescript
  import { Month } from './some/dir/month.ts';

  let month = new Month("June");

  // we need to imagine we have added some receipts to 'month'.
  
  console.log(month.receiptsChrono())
  // output: list of bills sorted chronologically
  ```

  As you can see, this code is probably more readable than using a dictionary and functions. You can still figure out what is going on, but we have been able to remove a few boilerplatey lines of code.


### Onwards!

This has been pretty off-the-cuff writing since I am excited to have found a use for classes in a project I am working on. I am looking forward to determining which methods will be useful for this class and am interested to see how the development of this app goes with a new tool to play with. Even as far as the output of this application goes, I am hoping to simply have a method that can be called as follows:

```typescript
console.log(month.output(format='csv'));
// output: a csv file of my data!
```

This post is proof that the [Self-taught Tech Network](https://discord.com/channels/932253730605252609) can help to up your coding game.

Until next time, keep fit and have fun.

![Hal Johnson and Joanne McCleoud in front of the Body Break logo](./bodybreak.webp)