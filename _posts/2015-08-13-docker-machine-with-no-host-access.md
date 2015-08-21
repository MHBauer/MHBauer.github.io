---
layout: post
title:  "docker machine with no host access"
date:   2015-08-03
categories: docker machine
---

I have full access to plenty of VMs. Set up with ssh and sudo. I do
not have access to the host. I can still use docker machine!

Use the `generic` driver, and make sure that the user that is given to sign in has paswordless sudo enabled.

