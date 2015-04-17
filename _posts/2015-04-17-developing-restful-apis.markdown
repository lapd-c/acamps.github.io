---
title: "Developing RESTful APIs"
layout: post
date: 2015-04-17 20:23:55
categories: api
---

When developing an [API][api] it is extremely important to think it through. To have a clear idea of how you want to structure the information.

Then, a key factor for an [API][api] to be used - both internally and externally- is for it to be _stateless_ and well-defined.

<blockquote><p>Whenever you can develop something stateless, do it, for your own mental health.</p><footer><cite>Albert Camps</cite></footer></blockquote>

With this, I mean that if you want to access a **product from a provider**, you should be able to do so with and [URL][url] that looks like: `/provider/:providerId/product/:productId`.

This clarity or simplicity is vital, and even you may not notice it, the fact that you don't depend on a first request is helpful.

[RESTful][restful] stands exactly for this two things that I just mentioned -and a few more-. That and the fact that the methods used are HTTP methods.

This kind of API's are really easy to use, and responses usually come structured in JSONS which are self-describing. A pleasure to work with.

Have you designed a RESTful API? Tell me about your experience!

[api]: http://en.wikipedia.org/wiki/Application_programming_interface
[url]: http://en.wikipedia.org/wiki/Uniform_resource_locator
[restful]: http://en.wikipedia.org/wiki/Representational_state_transfer
