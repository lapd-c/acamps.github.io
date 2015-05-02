---
layout: post
date: 2015-05-02 21:31:22
title: "Test Driven Development issues."
categories: tdd
tags: [test, test-driven-development]
---

If you don't work with [Test-Driven-Development][tdd] daily, you might now a few concepts, but you probably are not aware of all the things it implies.

I would love to see the results in the long run, but sincerely I have never had the chance.

## Issues
It is difficult to implement TDD, and here are the reasons why. Let's see if we can avoid a few, and make it easier for us to test.

### It's difficult to estimate.
When you work with SCRUM, you need to be able to _estimate_ the tasks. Having to test everything, sometimes sounds like it's not doable.

In most cases, **what you imagine impossible, is testable**, but it might be out of your technical knowledge.

#### Solution
Start testing on your own spare time, do the first versions so you can use your testing code for the new features.

Testing time will not be estimated because you will be spending your free time to test your code, but it will pay off.

### It is time consuming.
Testing requires time, and that's a fact. And if you modify old code and it has tests, it requires even more extra time. Besides, this time doesn't add any value to the product you are delivering.

_No one wants to see how awesome your tests are_.

#### Solution
**Tests help understand the code**. If you modify old code, you can use tests to see what it was doing.

The **time you spend with tests is time you spend understanding your code**. And moreover, often than you think you'll find small bugs, that otherwise would have slipped in the final product.

_No one wants to find bugs in the applications they use_.

----
At this point it looks like not testing is a lack of desire, or lack of _mental fortitude_ more than any other thing. So **no more excuses for not testing**.

Except that...  

## Why test?
Well, first and most importantly, because **it is your responsability**. You can not deliver code, and say _it works_ if you have no proof that it actualy does.

It's not professional, as [the Clean Coder](https://sites.google.com/site/unclebobconsultingllc/) postulates.

<blockquote><p>Be a damn professional programmer, otherwise you are hurting the image of us all. Don't hurt us.</p><footer><cite>Albert Camps</cite></footer></blockquote>

Do you develop using test-driven-development? How do you proceed?

[tdd]: http://en.wikipedia.org/wiki/Test-driven_development
