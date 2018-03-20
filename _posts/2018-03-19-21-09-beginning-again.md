---
layout: page
title: "Beginning again"
date: 2018-03-19T21:09:36Z
---

While I was debating where my afternoon had gone, I realized that the main thing I missed from the previous few days wasn't the goal of [$2117.91](https://richardlitt.github.io/2117.91USD), but the writing that I'd been doing - public, quick, to the point (more or less). I'd been able to very easily [rubber duck](https://www.wikiwand.com/en/Rubber_duck_debugging) myself by writing about what I was doing, and by making simple lists of things to help me along.

So, why not write this week, too? Even without a project, live blogging as I go along has proved to be helpful. This is different than journaling. I find that the latter tends to leave me getting too introspective, too fast, and it's hard for me to tie up passages and make them clear for myself later. The feel is different. However, writing for others - even when I barely let my fingers pause between sentences, like here - is the way to go.

That's what this blog is for. I set it up this afternoon, copying over the styles directly. Then I wasted an hour or so trying to get a subdomain working on [burntfen.com](https://burntfen.com), my default website. I don't think it'll work, after calling Hover and talking to them, and after continually googling how to do stuff on GitHub. That's probably OK. I set up [https://now.burntfen.com](https://now.burntfen.com) for people if they want to go to the most current project. My plan is to restart these journals either each week, or for each project.

For the past twenty minutes, I've been converting this template to be a bit more transferable for the next time I start one of these. There's at least one bit in my process I don't like - I don't want to run `rake post` too long before I publish, because then it'll be published with the timestamp of when I started the post, not when I ended it. I am writing this now in a `_drafts` folder in my `.gitignore`. I've just realized I can set up a Rake command called `publish` to automatically create a new post and move the draft to it, or to update the name of the file directly. I am going to do that now.

#### To Do

- [ ] Create a `rake publish` task, or die trying.