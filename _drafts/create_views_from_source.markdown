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
con esto, te dice el número de campos que tiene cada vista

Or create a way to count number of attributes from selects

http://dba.stackexchange.com/questions/23836/how-to-list-all-views-in-sql-in-postgresql
