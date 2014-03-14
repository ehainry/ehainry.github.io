---
layout: postsen
title: "Google also fails on standards"
categories:
- standards
- en
---

The google chrome team published a webbook entitled ["20 things I learned about browsers & the web"](http://www.20thingsilearned.com/). It's nice and pretty with beautiful drawings and interesting content. However, there was a distasteful yellow header on the page while I was viewing the page in my current browser of choice: [luakit](http://luakit.org/) telling me that I needed a modern browser to see the book and all its features:

![luakit](http://velsheda.lateralis.org/journal/images/luakit_20.png)

Well, luakit may not support everything I guessed. Let us use firefox (well technically, iceweasel but it's just firefox with another name, it should be recognized as firefox by any intelligent website). Same verdict:

![iceweasel](http://velsheda.lateralis.org/journal/images/iceweasel_20.png)

OK, I followed the link at the top telling me what modern browsers meant. It listed firefox but also opera. I like opera. And I have the latest alpha of it. Just let me launch it and... nothing better:

![opera](http://velsheda.lateralis.org/journal/images/opera_20.png)

So I guess they do user-agent sniffing and they are bad at it. Let us try luakit with chrome's user-agent string. Hey it works! And there is a new feature: some kind of red bookmark that shows sharing possibility when I hover it...

![luakit as chrome](http://velsheda.lateralis.org/journal/images/luakit_as_chrome_20.png)

Conclusion: still the same: sniffing user-agent is bad: it prevents my browser from doing what it can do and you pretend it cannot. Please don't do it (and if you are Apple or Google, be fair to your competitors).
