---
layout: post
title: "Generate Queries From SQL"
date: 2015-05-05T23:18:43+02:00
categories: sql
---

In SQL you can generate your own queries, which comes in handy when you have to operate with all the tables from your database.

All in all, you can use simply a concatenation operand and a [subselect][article] to get your results.

For example, if we have the tables from the database `tickit` and schema `dragon` in the [following query](http://docs.aws.amazon.com/redshift/latest/dg/c_join_PG_examples.html):

{% highlight sql %}
select datname, nspname, relname, sum(rows) as rows
from pg_class, pg_namespace, pg_database, stv_tbl_perm
where pg_namespace.oid = relnamespace
and pg_class.oid = stv_tbl_perm.id
and pg_database.oid = stv_tbl_perm.db_id
and datname ='tickit'
group by datname, nspname, relname
order by datname, nspname, relname;
{% endhighlight%}

Then we might be interested in granting select to one user on all the tables from one schema.

We cannot do that directly, but we can:

{% highlight sql %}
select 'GRANT SELECT on table ' || nspname || '.' || relname || ' to user_name;'
from (
    select datname, nspname, relname, sum(rows) as rows
    from pg_class, pg_namespace, pg_database, stv_tbl_perm
    where pg_namespace.oid = relnamespace
    and pg_class.oid = stv_tbl_perm.id
    and pg_database.oid = stv_tbl_perm.db_id
    and datname = 'tickit'
    and nspname = 'dragon' 
    group by datname, nspname, relname
    order by datname, nspname, relname
)
;
{% endhighlight %}

This will generate all the queries we need. After this it's just a matter of executing them.

If you are not on Redshift, you can convert this to a prepared query using directly the into command, and then execute the query automatically. On Redshift you need a bit of copy and paste.

<blockquote><p>Create query generators always instead of changing small things one by one. You'll be less error prone, and it's much more satisfying.</p><footer><cite>Albert Camps</cite></footer></blockquote>

Have you generated interesting queries? How you generate them?
