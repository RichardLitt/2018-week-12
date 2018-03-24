---
layout: page
title: "An audit of the node.js i18n groups"
date: 2018-03-23T22:19:25Z
image: /assets/img/logo.png
---

Let's check in on the [Node.js i18n committee](https://github.com/nodejs/i18n). I want to run [`name-your-contributors`](https://github.com/mntnr/name-your-contributors/) on the translation repos to see if there has been activity recently, now that I've cleaned up NYC this week (yesterday morning). This was suggested [here](https://github.com/nodejs/i18n/issues/19).

So, I went and built a shell script that automatically pulls data - comments, PRs, and reviews - from Node's 15 or so i18n repositories, from the past year. I used `jq` to filter the JSON objects I got back, and used some really basic shell scripting to print it out into a nice Markdown file that I could plop into the issue. All in all, it took around an hour - and now we know more about the activity in those repositories, and I know that name-your-contributors can be used for some pretty cool statistics.

Since GitHub repos are cheap, I uploaded all of the code [here](https://github.com/RichardLitt/node-i18n-audit). I'm feeling pretty proud about this one. Here's an example of a result:

---

## nodejs/nodejs-de audit

_This list was automatically generated with the following command:_

```sh
$ name-your-contributors -u nodejs -r nodejs-de -a 2017-03-01
```

There were 3 issue commentators who made 6 comments.
There were 0 reviewers who made null review comments.
There were 0 issue creators who made null issues.
There were 2 PR commentators who made 2 comments.
There were 1 PR creators who made 1 prs.

---

It's pretty clear from this that there just wasn't much activity - no new issues, only one new PR. Hopefully we can do better in the future!

I am going to take a break and move around; time to pack for my trip to Vermont tomorrow.
