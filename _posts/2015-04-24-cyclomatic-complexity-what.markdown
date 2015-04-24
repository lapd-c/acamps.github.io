---
layout: post
title: "Cyclomatic Complexity What?"
date: 2015-04-24T20:30:07+02:00
categories: programming
tags: [programming, code-quality]
---

A few days ago, as I was working on a _complex_ function, I got a warning from [PHPStorm][phpstorm] that the [cyclomatic complexity][complex] of that function had reached the stablished complexity level of 10. "This must be bad" - I thought, without a clue why.

So, what is this [cyclomatic complexity][complex] exactly?

If you already checked the links pointing to the wikipedia for the term, you can have a vague idea, or like me the first two times I checked **no idea at all**.

I would define it as:

<blockquote><p>Cyclomatic complexity is a measure of the quantity of different ways your code can execute. Complex code is difficult to maintain. That's bad. </p></blockquote><footer><cite>Albert Camps</cite></footer></blockquote>

So the more ifs and loops your code has, the more _complex_ it is.

## How can I reduce the cyclomatic complexity?

Well, so we learnt that having a high cyclomatic complexity is **bad**. How to get rid of it?

And as you would _never imagine_ the anwer is: **refactoring**.

In this case, you usually can use the [extract method][extract] refactor. And extracting a few conditions and loops made the code much more readable.

So my code wasn't extremely bad after all.

What do you do to check the quality of your code? Is there any other metric that you use to check your code?

[complex]: http://en.wikipedia.org/wiki/Cyclomatic_complexity
[extract]: http://refactoring.com/catalog/extractMethod.html
[phpstorm]: https://www.jetbrains.com/phpstorm/
