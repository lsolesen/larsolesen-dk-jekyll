---
title: "Struggling with duplicate content in Drupal 7"
permalink: /content/struggling-duplicate-content-drupal-7
language: und
tags:
  - drupal
  - planet drupal
modified: 2011-12-09T10:21:23Z
---

I struggled many hours to improve the technical side of SEO on [Vejle Idrætshøjskole](http://vih.dk)s website. Here is what I discovered:

Google Webmaster Tools showed me duplicate content
--------------------------------------------------

After reviewing Google Webmaster Tools (under Diagnose --> HTML suggestions) I discovered that I had quite a lot of duplicate content, mainly caused by Views adding order- and sort-parameters to the query, thus making Google index basically the same page twice. Allthough, it seems that [Google doesn't think webmasters should make special measures anymore](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=66359), I do not like having my pages indexed twice.

There is also a [discussion at drupal.org which addresses the problem about duplicate content](http://drupal.org/node/345620), as I discovered.

Blocking duplicate links in robots.txt
--------------------------------------

To avoid the links introduced by views being indexed by Google, I entered the following in my robots.txt.

```
Disallow: /*sort=
Disallow: /*order=
Disallow: /*page=1
```
In a week or so, I hope that I will be rid of all the duplicate content created by the extra parameters views adds to the links.

Views should not default to base view
-------------------------------------

Having setup a Views page on e.g. example.com/nyheder will automatically make requests like example.com/nyheder/34 show the base view url. To avoid this, you need to setup contextual filters on your views. I just leave everything to the basic settings, except I will add a validation rule. If the validation does not pass, I will show a 404. That, I hope, basically solved my biggest problem with duplicate content. And hopefully whis will make Google very happy and will award me some SEO LOVE.

What are you doing to avoid duplicate content?
