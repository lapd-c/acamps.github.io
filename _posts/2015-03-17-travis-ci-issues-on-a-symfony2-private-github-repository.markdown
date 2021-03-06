---
title: "Travis CI issues on a Symfony2 private Github repository"
layout: post
date: 2015-03-17 21:35:23
categories: testing travis symfony2
---

I just ended the integration of one of our applications with [Travis CI][travis], and man it has been fun. We are very lucky that our company - [Social Point](http://engineering.socialpoint.es) - provides all the tools we want for improving code quality purposes, so they made [Travis CI][travis] available to all of us. Then I started spending a few spare moments on configuring this _fantastic_ tool, just for the fun of it.

The premises were _**easy**_:

* Configure an automated environment for testing in your projects
* You are done!

It might look like it was a 15 minutes task, but it was **not**. A few problems arose.

### Error missing bootstrap.php.cache (not found)
[Travis CI][travis] log was complaining that it was unable to find the `bootstrap.php.cache` file. Since I know this file should be auto-generated, this was _weird_.

In the end I discovered it was due to the fact that we have a peculiar structure in this particular project.

The [symfony2][symfony] project is contained in a `Symfony` folder, so I needed to add the following code, in order to work straight like the examples you can find around the net. How silly.

```
before_script:
  - cd Symfony
```

As a wise man once said:

<blockquote>
  <p>
    Never <strong>ever</strong> use custom folder structures. Unless you like pain.
  </p>
  <footer><cite title="Albert Camps">Albert Camps</cite></footer>
</blockquote>

### Fatal error: Class 'Symfony\Bundle\FrameworkBundle\Test\WebTestCase' not found
This error occurred in one of my desperate efforts to solve the previous error.

I tried to remove the `bootstrap = "bootstrap.php.cache"` comment in `phpunit.xml` and `phpunit.xml.dist`.

It doesn't work out, when composer gets properly executed in your home folder, it will give you your desired `bootstrap.php.cache`.

As per Symfony2 2.4 you can execute the following to create again a `bootstrap.php.cache` file.

```bash
cd vendor/sensio
php SensioDistributionBundle/Resources/bin/build_bootstrap.php
```

### Issues with tests using `file_get_contents`
When you think all your tests should pass and they don't, what an amazing moment. The world unwraps before your eyes.

I don't know how, exactly, but a few paths were with some caps switched, and our development environments, **were accepting wrong paths**.

Obviously [Travis][travis] was not that _nice_, and it complained, that files could not be found. It was a **silly** switched-caps mistake, but difficult to spot.

**Watch out** your `file_get_contents` since they may include misspells that determinate `php.ini` configurations may accept, but not the production nor [Travis][travis] environment.

### Issues with Symfony2 version on composer.json
A few issues solved, a few more to go.

Out of nowhere [symfony2][symfony]'s composer decided to stop working due to some strange dependencies issue.

Googling around I stumbled upon [this github issue](https://github.com/symfony/AsseticBundle/issues/223) that explains the issue and suggests adding the following `require` code to your `composer.json`:

```
"minimum-stability": "dev",
"require": {
    "symfony/assetic-bundle": "2.3.*@stable",
    "kriswallsmith/assetic": "1.1.x@stable"
}
```

### Github limited number of requests
And just when I thought that everything was working fine, my fast hands did a few more pushes than they should an **TADA!!** a new error specifying that the sources were not available.

_**Why?**_ Because Github limits the amount of requests unauthenticated users can perform. Luckily the work around has been easy to implement, thanks to this [gist](https://gist.github.com/h4cc/7680054).

First we need to generate our **token**, that will authenticate us and increase our limit from 60 to 5000 requests:

```bash
curl -u 'githubuser' -d '{"note":"Your Application"}' https://api.github.com/authorizations
```

Then we add yet another `before_script` step to the configuration in order to set up our freshly cropped Github token:

```
  - travis_retry composer config --global github-oauth.github.com tokeNtokEntoKentOkenToken
```

As a side note, changing `composing install --prefer-dist` to `composer install --prefer-source` _may_ eradicate this problem altogether as mentioned in this [page](http://help.pagodabox.com/customer/portal/questions/6193893-failed-to-download-doctrine-common-from-dist-could-not-authenticate-against-github-com).

----

It hasn't been easy to sort everything out, but now it's done, I feel fantastic. After all issues faded, I wanted to include at least one improvement.

**SPEED**

### Add cache for faster enviroment execution
In the [docs]() you can find how to add a cache, and that this might speed up your build processes.

This was inspired by [yii2 repo](https://github.com/yiisoft/yii2/blob/2.0.3/.travis.yml) and is done by the following code:
```
cache:
  directories:
    - Symfony/vendor
    - $HOME/.composer/cache
```

### How it adds up
```
language: php

php:
  - 5.4
  - 5.5
  - '7'

env:
  - SYMFONY_VERSION=2.4.*
  - SYMFONY_VERSION=dev-master


before_script:
  - cd Symfony
  - travis_retry composer self-update && composer --version
  - travis_retry composer config --global github-oauth.github.com tokeNtokEntoKentOkenToken
  - travis_retry composer require symfony/symfony:${SYMFONY_VERSION}
  - travis_retry composer install --no-interaction --prefer-dist

script: bin/phpunit --coverage-text -c app

matrix:
  allow_failures:
    - env: SYMFONY_VERSION=dev-master
```

### Final considerations
All in all, a lot of easy-to-avoid mistakes, and a bit of learning for future uses. My new challenge will be integrating this into a **python** project that we have.

As you can see, this executes simultaneously the tests for 3 different versions of php and 2 different [Symfony2][symfony] environments, allowing failures on one of this environments. Very intuitive, very cool.

Also, there are issues that I thought I would find, that I didn't. Let's keep [this](http://vvv.tobiassjosten.net/symfony/continuous-integration-for-your-symfony2-app/) handy anyway.

Different to setting up a [Jenkins](http://jenkins-ci.org/) server, but fun nevertheless.

[travis]: http://www.travis-ci.com
[symfony]: http://symfony.com/
