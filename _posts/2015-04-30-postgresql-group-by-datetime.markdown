---
layout: post
title: "PostgreSQL - Group by Datetime"
date: 2015-04-30T20:54:03+02:00
categories: sql, postgresql
tags: [sql, postgresql, redshift]
---

If you have ever tried to group a table by a _datetime_ field you probably have noticed that you are not able to do so.

{% highlight sql %}
select datetime, sum(amount) from t_buys group by datetime;
{% endhighlight %}

Will result in an error.

If the table we are querying contains rows with recent datetimes, and you want to group by day, I recommend using `date_part`  with `dayofyear`.

{% highlight sql %}
select date_part(dayofyear,datetime), sum(amount) from t_buys group by date_part(dayofyear,datetime);
{% endhighlight %}

The result to this query will contain, in the first row a number from 1 to 366. And in the second row, the total amount for that day.

If you have data that is from more than 366 days, obviously you will need to add a third column containing the year. But in this scenario, I would recommend directly:

{% highlight sql %}
select date_part(y, datetime), date_part(mon, datetime), date_part(d, datetime), sum(amount) from t_buys group by date_part(y, datetime), date_part(mon, datetime), date_part(d,datetime);
{% endhighlight %}

<blockquote><p>Get to know your functions. Probably someone thought about what you want before you did.</p><footer><cite>Albert Camps</cite></footer></blockquote>

Which _SQL_ tricks do you usually do?
