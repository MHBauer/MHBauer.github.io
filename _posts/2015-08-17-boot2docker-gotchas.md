---
layout: post
title:  "boot2docker gotchas"
date:   2015-08-17
categories: golang virtualbox
---

when using boot2docker with virtualbox, your home directory is mounted inside of the host VM. This is useful and confusing and dangerous and deceptive. I would rather it was not a default option, or that the shared directories were read only, and not read/write. 
