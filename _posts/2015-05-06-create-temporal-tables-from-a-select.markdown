---
layout: post
title: "Create Temporal Tables From a SELECT"
date: 2015-05-06T23:16:31+02:00
categories: sql
tags: [sql]
---

Some times you want to iterate with your results from a query and do a few operations on them before having them as a definitive result.

This can be easily done with the `INTO` clause that works a bit different depeneding on which provider of SQL you are relying.

In Redshift's PostgreSQL you can:

{% highlight sql %}
SELECT user_id into temp new_users from users where date_register > '2015-04-10';
{% endhighlight %}

The good thing about this temporal table is that as long as you don't disconnect, you can play with it as much as you like.

And you don't need to worry about space in the database itself because all will disappear when your session ends.

<blockquote>Before working with your data shape it correctly. Don't waste time nor space.<p></p><footer><cite>Albert Camps</cite></footer></blockquote>

You can create temporal tables too direclty and then work with them as usual tables.

This is really usefull if you want to do complex data manipulations. It is much clearer than a lot of nested subqueries.

How do you use temporal tables in your work?
