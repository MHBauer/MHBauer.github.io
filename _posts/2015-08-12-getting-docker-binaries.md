---
layout: post
title:  "getting docker binaries"
date:   2015-08-12
categories: docker
---

I am on osx, and I want to get a new binary in one step after I modify the code.

I can run `make cross`, but that leaves the binary inside of a container.

I wrote this script to build an image and run it, then `docker cp` the
binary out when it is finished. There is an attempt at cleanup, but no
error checking.

<script
src="https://gist.github.com/MHBauer/a9092932378f54f4890a.js"></script>

Suggestions welcome.
