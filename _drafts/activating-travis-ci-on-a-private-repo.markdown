---
title: "Activating-travis-ci-on-a-private-repo"
layout: post
---
http://russellscottwalker.blogspot.com.es/2014/01/phpunit-cannot-open-file-bootstrapphp.html
http://docs.travis-ci.com/user/languages/php/
http://vvv.tobiassjosten.net/symfony/continuous-integration-for-your-symfony2-app/

http://symfony.com/doc/current/cmf/components/testing.html

Error missing bootstrap.php.cache (not found)
Fatal error: Class 'Symfony\Bundle\FrameworkBundle\Test\WebTestCase' not found

Use composer install

https://github.com/okulbilisim/ojs -- as a reference
http://php-and-symfony.matthiasnoback.nl/2011/10/symfony2-use-a-bootstrap-file-for-your-phpunit-tests-and-run-some-console-commands/ -- more info in bootstrappin

https://github.com/symfony/AsseticBundle/issues/223 -- Issues with symfony

issues with tests using `file_get_contents`

Adding a cache https://github.com/yiisoft/yii2/blob/master/.travis.yml

Github limiting the number of requests --> change to prefer source.
https://github.com/composer/composer/issues/1861
http://help.pagodabox.com/customer/portal/questions/6193893-failed-to-download-doctrine-common-from-dist-could-not-authenticate-against-github-com
https://gist.github.com/h4cc/7680054

276154a26e4a45c72b4ca139c3afd19fc4d08c9c
