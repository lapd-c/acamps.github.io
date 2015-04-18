---
title: "Create views from source"
date: 2015-04-18 20:43:12
layout: post
categories: sql postgresql
---

In SQL it is important to know that there are things that look not automatable but they surprisingly are.

For example, you can generate queries from plain SQL, using a specially formatted SELECT. If executed directly produce the views.

We first explore `pg_views`.

{% highlight sql %}
SELECT * FROM pg_views;
{% endhighlight %}

The `description` field contains the rest of the query.

{% highlight sql %}
SELECT 'CREATE VIEW '+schemaname+'.'+viewname' AS '+description+';' as query from pg_views;
{% endhighlight %}

Of course, you might want to check whether the amount of fields is still the same. The following query helps you find out that.

{% highlight sql %}
SELECT n.nspname AS table_schema,
 pg_catalog.pg_get_userbyid(c.relowner) AS table_owner,
 c.relname AS table_name,
 COUNT(a.attname) AS column_count,
 pg_catalog.obj_description(c.oid,'pg_class') AS comments,
 CASE c.relkind
 WHEN 'v' THEN pg_catalog.pg_get_viewdef (c.oid,TRUE)
 ELSE NULL
 END AS query
FROM pg_catalog.pg_class c
 LEFT JOIN pg_catalog.pg_namespace n ON (n.oid = c.relnamespace)
 LEFT JOIN pg_catalog.pg_attribute a
 ON (c.oid = a.attrelid
 AND a.attnum > 0
 AND NOT a.attisdropped)
 LEFT JOIN pg_catalog.pg_stat_all_tables s ON (c.oid = s.relid)
WHERE c.relkind = 'v'
GROUP BY n.nspname,
 c.relowner,
 c.relkind,
 c.relname,
 c.oid
ORDER BY n.nspname,
 c.relname;
{% endhighlight %}

When I have more time, I would love to create a query that can generate the VIEW with the column separated, not only inside the SELECT clause.

<blockquote><p>Always have a SQL trick up your sleeve. You'll need it sooner than you expect.</p><footer><cite>Albert Camps</cite></footer></blockquote>

What magic queries do you have? What are you capable of?
