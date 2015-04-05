---
title: "Connect to Redshift from R"
date: 2015-04-05T19:06:49+02:00
layout: post
categories: redshift r
---

If you want to connect to [Redshift][redshift] in [RStudio][rstudio], the best way to do may very well be with first to remember that [Redshift][redshift] is a [Postgresql][psql] database.

That helps us position ourselves into using [RPostgreSQL](http://cran.r-project.org/web/packages/RPostgreSQL/index.html), a fantastic library that makes our lifes easier.

**But**, as it offen happens, things don't work out of the box. First of all, the latest version of R is not able to install the package via the usual command:

{% highlight r %}
install.packages("RPostgreSQL")
# But this will throw an error. Not binary available
# So let's check the source
install.packages("RPostgreSQL",type="source")
{% endhighlight %}

Will throw another error anyway. It complains about missing `"libpq-fe.h"`. Since an `*.h` file looks more like dependency failing, we thought that this might be due to the fact that we didn't had [PostgreSQL][psql] installed in our machines. We solved this easily with:

{% highlight bash %}
$ brew install postgresql
{% endhighlight %}

Once we have PosgreSQL installed we can run again:

{% highlight r %}
install.packages("RPostgreSQL",type="source")
{% endhighlight %}

And you can happily `library("RPostgreSQL")`.

As a side note, you can also find [pingles/redshift-r][repo], which we weren't able to make work :(

[repo]: https://github.com/pingles/redshift-r
[rstudio]: http://www.rstudio.com
[redshift]: http://aws.amazon.com/redshift/
[psql]: http://www.postgresql.org/ 
