---
layout: page
title: "Using Rake to publish a post"
date: 2018-03-19T21:35:14Z
---

Well, that was easier than I thought. I realized I didn't have to make another rake task at all; I could just use my old `rake post title="title"` command, and add a bit where it reads my draft's contents into the new post, and then starts a commit for me. I didn't know how to do this in Rake - five minutes of reading the manuals tells me it can include shell commands easily. So, that's surprisingly easy. Done.

I've rigged it to commit my post, too. I'll need to add a tool that automatically tweets it if I send a flag. Or I could use IFTTT. Or I could just tweet manually.