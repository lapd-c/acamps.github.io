---
title: "Select all views in Redshift"
layout: post
date: 2015-03-26 23:33:21
categories: redshift
---

When you need to select views in [Redshift][rs] the easiest way is to:

```sql
select * from pg_views;
```

This table also contains the schema where the tables are, and the code for generating them.

But if you are not able to discover the `pg_views` table exists, or if you need different information you can also find information about the views at:

```sql
SELECT DISTINCT 
    srcobj.oid AS src_oid
    ,srcnsp.nspname AS src_schemaname
    ,srcobj.relname AS src_objectname
FROM
    pg_catalog.pg_class AS srcobj
INNER JOIN
    pg_catalog.pg_depend AS srcdep
        ON srcobj.oid = srcdep.refobjid
INNER JOIN
    pg_catalog.pg_depend AS tgtdep
        ON srcdep.objid = tgtdep.objid
LEFT OUTER JOIN
    pg_catalog.pg_namespace AS srcnsp
        ON srcobj.relnamespace = srcnsp.oid
WHERE srcobj.relkind = 'v' --v= view;
```

This is a modification of the code found publicly available in [awslabs/amazon-redshift-utils][repo] and is hereby presented under the same license I received the code. [Amazon's license][license].

In the mentioned repository, you can also find an sql sentence for finding dependencies between views. Which I will cover in a next post.

<blockquote>
<p> SQL stands for Satanic Query Language. Just joking. Or not.</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

Do you have to deal with Redshift frequently? Which are your favourite attributes about it?

[license]: http://aws.amazon.com/asl/
[repo]: https://github.com/awslabs/amazon-redshift-utils
[rs]: http://aws.amazon.com/redshift/