---
layout: post
title: "PostgreSQL - Sub Select"
date: 2015-05-01T23:59:48+02:00
categories: sql
tags: [sql]
---

When analysing data, sometimes you can have a big amount of data to analyse, and in this scenario it is important to chose the right moment when to import the data into your local machine to work.

If you have too much data, your machine might not be able to handle it correctly.

In this scenario it can be better to first filter through enough with sub selects.

{% highlight sql%}
select user_id, sum(custom_attribute) from (select user_id, attribute as custom_attribute from table_ten where attribute = value) group by user_id;
{% endhighlight %}

The idea behind this is that the **inner query** aims to create a _temporal table_ with the query below. It goes inside the from clause.

{% highlight sql%}
select user_id, attribute as custom_attribute from table_ten where attribute = value;
{% endhighlight %}

This acts as a table where the columns are the attributes you have in the select clause.

Then you can act as normal, as if it were a normal table. And then you only import in your computer the smallest amount of data possible.

<blockquote><p>Only import the data you need. Having extra data will make it harder to actually do your work with the data.</p><footer><cite><Albert Camps</cite></footer></blockquote>

Do you use subselects in your daily work? Which tricks do you use?
