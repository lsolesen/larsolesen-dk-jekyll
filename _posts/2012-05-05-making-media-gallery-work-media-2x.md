---
title: "Making Media Gallery work with Media 2.x"
permalink: /content/making-media-gallery-work-media-2x
language: und
tags:
  - drupal
  - planet drupal
last_modified_at: 2012-05-05T10:25:34Z
---

I am constantly trying to make it easier to be an editor at Vejle Idrætshøjskole site. Now the time has come to make it easier to create photo galleries. Earlier I uploaded the photo galleries to Picasa Web and created a [custom input filter](http://drupal.org/project/picasa_slideshow_filter), which could embed the photo galleries as a slideshow into the page and used [PWI](http://code.google.com/p/pwi/) to embed a photo gallery.

However, when watching the editors doing that, I just knew that I had to change the approach.

Enter media gallery
-------------------

I had my eye out for media gallery for quite some time, but was reluctant to use it seeing the [issue queue](http://drupal.org/project/issues/media_gallery?categories=All). However, watching [screencasts](http://www.youtube.com/watch?v=0nA7Xjq66DI) I decided I would go for it anyways. Maybe I could help solve some of the issues.

My first problem was that I use the Media 2.x-branch, and media gallery only works for the 1.x-branch at the moment. Luckily, [I was not the only one needing media gallery to work with 2.x](http://drupal.org/node/1244204). I started [creating](http://drupal.org/files/install-on-media-2x-branch.patch) [some](http://drupal.org/files/open-addimage-popup-issue-1244204-comment-40_0.patch) [patches](http://drupal.org/files/changed-formatter-to-file-issue-1244204-comment-41.patch) which made it possible to have media gallery installed, but it was still not possible to add images to the galleries.

So this is where open source is great. [leschekfm](http://drupal.org/user/264153) took my patches and made it possible to add files to the media gallery.

How to make media gallery work for the media 2.x branch
-------------------------------------------------------

Media gallery still does not have a 2.x-branch. But to have media gallery work anyways, I did the following:

```
$ git clone --recursive --branch 7.x-1.x http://git.drupal.org/project/media_gallery.git
$ cd media_gallery
$ git apply http://drupal.org/files/fixed-media-adding-and-multedit-1244204-comment-42.patch
```

I only needed one patch, because leschekfm put my three patches into his, which makes testing a lot easier.

I also needed to install the required multiform module.

```
$ drush dl multiform
$ drush en multiform
```

Then for ease of upload, I installed plupload to make it easier to upload all the files at once.

```
$ drush dl plupload
$ drush en plupload
$ cd sites/all/libraries/
$ wget https://github.com/downloads/moxiecode/plupload/plupload_1_5_4.zip
$ unzip plupload_1_5_4.zip
```

So that is basically all there is to having media gallery work with media 2.x-branch.

Now we are just hoping for the developers of media gallery, that they will open up the 2.x-branch of media gallery, so the community can start helping out.
