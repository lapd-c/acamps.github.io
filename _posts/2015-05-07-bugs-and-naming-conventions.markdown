---
layout: post
title: "Bugs and Naming Conventions"
date: 2015-05-07T23:25:41+02:00
categories: bugs
---

If you work in projects that involve intensive use of databases it is more likely than not that you have stumbled upon variables with confusing names.

I even once heard about a mysterious field callet `trumpet` that noone ever knew what was used for.

So even if it's primarily informal, I recommend very much the **use of a document that defines _convention names_**.

What is commonsense for someone, might not be for others, and since usually more than one person is dealing with the components, it's good to have clear indications about how to do so.

<blockquote><p>Don't suppose others have common-sense. They don't.</p><footer><cite>Albert Camps</cite></footer></blockquote>

Finally, another option is to [comment](http://docs.aws.amazon.com/redshift/latest/dg/r_COMMENT.html) the database. Most vendors SQL, has this function that allows adding comments to the table, so they can be read in moments of need. 

As it often happens, the complication with this ends up being maintenance.

Do you have a document for naming conventions? How you handle this issue?
