---
title: "Understanding the power of Barracuda"
permalink: /content/understanding-power-barracuda
language: und
tags:
modified: 2012-12-02T20:37:27Z
---

There is several ways you can use Barracuda. I am trying to find the most efficient ways, both as a developer and to utilize the server ressources efficiently.

This is my journey.

First approach: Create one platform pr. site
--------------------------------------------

Usually I have created [each](https://github.com/vih/vih.dk-deploy) of [my](https://github.com/motionsplan/motionsplan.dk) [sites](https://github.com/dantechdk/dantechdk-deploy) as an [install](https://github.com/lsolesen/teambuilder.vih.dk) profile, so I could easily build them on my Aegir server and locally for development. I also have separate code bases, so changes to the platform will not break other sites.

To create a platform for my site, I would just build it using drush make:

```
<pre style="margin-top: 15px; margin-bottom: 15px; padding: 6px 10px; border: 1px solid rgb(204, 204, 204); font-size: 13px; font-family: Consolas, 'Liberation Mono', Courier, monospace; background-color: rgb(248, 248, 248); line-height: 19px; overflow: auto; border-top-left-radius: 3px; border-top-right-radius: 3px; border-bottom-right-radius: 3px; border-bottom-left-radius: 3px; color: rgb(51, 51, 51);">
`drush make larsolesen_dk.build /data/disk/o1/static/larsolesen_dk_build`
```
However, one of the advantages of using Barracuda is having a shared codebase and thus a shared code cache, so I am trying to get a hold of a new workflow.

Second approach: Create several install profiles in the same platform
---------------------------------------------------------------------

I should be sharing more code. E.g. this [site](http://github.com/lsolesen/larsolesen.dk), [motionsplan.dk](http://github.com/motionsplan/motionsplan-deploy), [dantechdk.com](http://github.com/dantechdk/dantechdk-deploy) and [insitu-duo.dk](https://github.com/mikaelbirkelundjohansen/insitu-deploy) are all based on a regular Drupal. However, I have created separate installation profiles for each site to keep track of the code needed. However, in Barracuda you should really use the builtin platforms if possible.

This will be better, as I am now sharing the entire Drupal-codebase between the sites. This would still be very easy, as I could just clone my install profile into the built-in platform in the /profiles directory, and then from profiles/larsolesen\_dk run:

```
<pre style="padding: 6px 10px; font-size: 13px; font-family: Consolas, 'Liberation Mono', Courier, monospace; background-color: rgb(248, 248, 248); margin-top: 15px; margin-bottom: 15px; overflow: auto; border: 1px solid rgb(204, 204, 204); line-height: 19px; border-top-left-radius: 3px; border-top-right-radius: 3px; border-bottom-right-radius: 3px; border-bottom-left-radius: 3px; color: rgb(51, 51, 51);">
`drush make --no-core --contrib-destination=. larsolesen_dk.make`
```
This is stil very clear, and all the code is in version control easily to understand.

However, there is still a lot of code which could be shared, e.g. views, pathauto, redirect, wysiwyg and other contrib modules, that I use on all of my sites.

Third approach: Create all install profiles in one platform and share contrib
-----------------------------------------------------------------------------

I extracted the common modules and put it into a drush make file. That file I would just include in the build file for my install profiles like this:

```

includes[] = https://raw.github.com/lsolesen/buildthat/7.x-1.x/buildthat.make
```
Now these will go into sites/all module, so the contrib modules will also be shared. All by install profiles with their custom modules will go into sites/sitename.dk.

Now I have a platform where all code is shared except the custom code for the particular site.

I have created a [make file which can pull in all my install profiles into the same platform build on github.com](https://github.com/lsolesen/boa-makefiles). Just running that drush make file will build a custom platform, where the core Drupal code and contrib modules are shared between sites.

Fourth approach: Share even more code between the sites in builtin platforms
----------------------------------------------------------------------------

Barracuda comes with a bunch of built-in platforms, e.g. a regular Drupal. And it shares the code even between octopus instances. I should really use some of those. Most of my sites is just based on a regular Drupal, so I will use that as an example.

But how will I actually get the code in there.

If I still want to build the sites of the built-in Drupal-install, I should put the shared contrib code into /sites/all/modules, /sites/all/libraries and /sites/all/themes. I could create my own make file to pull in the dependencies, I use on most of my sites and use the drush command above to get the modules into the correct space, like like [buildthat](https://github.com/lsolesen/buildthat/blob/7.x-1.x/buildthat.make). That I would need to do manually going into the sites/all folder and running:

```
<pre style="padding: 6px 10px; font-size: 13px; font-family: Consolas, 'Liberation Mono', Courier, monospace; background-color: rgb(248, 248, 248); margin-top: 15px; margin-bottom: 15px; overflow: auto; border: 1px solid rgb(204, 204, 204); line-height: 19px; border-top-left-radius: 3px; border-top-right-radius: 3px; border-bottom-right-radius: 3px; border-bottom-left-radius: 3px; color: rgb(51, 51, 51);">
`drush make --no-core --contrib-destination=. `https://raw.github.com/lsolesen/buildthat/7.x-1.x/buildthat.make
```


But then all the sites have their own custom modules. These should probably go into sites/sitename.dk/modules, but that is discouraged for more reasons. 

- They could be pulled in there with a make file and using the same drush command as above, but the site would need to be available before you could do that.
- On migration or cloning these modules are just tarballed "as is", and having modules in this space there is no reliable rollback in Aegir, so that is not the best place to keep those modules.

So should these modules also go into the sites/all space and thus be available to all sites? That seems odd, if you have a custom module aimed at [exercises](http://github.com/motionsplan/motionsplan_exercise).

Minor Drupal updates: What when?
--------------------------------

Now let's say I need to upgrade minor version of Drupal. I would create the regular Drupal platform. Then I would pull in the shared contrib modules in sites/all. I would then migrate all the sites to the new platform. After that I would create a similar platform just with updated shared contrib modules, and move all my sites again. I would have updated sites easily running on the same platform.

Contrib module updates: What when?
----------------------------------

When the contrib modules are updated, I could do the same thing, and the migrate all the sites one by one to the new platform build with the upgraded modules. However, that is not possible with the built-in platform, as you cannot use the same platform twice. Then I would need to do the module upgrading directly in the built-in platform.

Custom modules upgrade: What when?
----------------------------------

The question is still the custom modules. How will I be able to upgrade them safely?
