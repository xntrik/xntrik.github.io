---
layout: post
status: publish
published: true
title: Recent Readings on App Sec, CI, Apple's OS', Freedom and Cyberpunk
permalink: readings-app-sec-ci-apple-os-freedom-cyberpunk
author:
  display_name: Christian
  login: xntrik
  email: xntrik@un-excogitate.org
  url: ''
author_login: xntrik
author_email: xntrik@un-excogitate.org
wordpress_id: 747
wordpress_url: http://un-excogitate.org/?p=747
date: '2013-01-04 13:45:09 +0000'
date_gmt: '2013-01-04 05:45:09 +0000'
tags:
- owasp
- web application
- Security
- ruby
- development
- cyberpunk
- ci
- rails
- books
- apple
- rugged
comments:
- id: 99418
  author: un-excogitate.org &raquo; Blog Archiv &raquo; Recent Readings on BeEF, MetasploiTor,
    Automation, SDLCs, Phishingggggggg
  author_email: ''
  author_url: http://un-excogitate.org/archives/2013/01/18/recent-readings-on-beef-metasploitor-automation-sdlcs-phishingggggggg/
  date: '2013-01-18 14:15:55 +0000'
  date_gmt: '2013-01-18 06:15:55 +0000'
  content: "[...] few different open source security automation projects going on
    at the moment (I mentioned Codesake recently), but this one looks pretty interesting.
    It seems to be fairly modular (currently appears to [...]"
- id: 100118
  author: Paolo
  author_email: paolo@armoredcode.com
  author_url: http://armoredcode.com
  date: '2013-01-22 00:51:47 +0000'
  date_gmt: '2013-01-21 16:51:47 +0000'
  content: "Man, thank you so much for having spent beautyful words for codesake that
    is in very early stage.\r\n\r\nI do hope it could turn in something useful :)"
- id: 100177
  author: Christian
  author_email: xntrik@un-excogitate.org
  author_url: ''
  date: '2013-01-22 09:10:28 +0000'
  date_gmt: '2013-01-22 01:10:28 +0000'
  content: No worries Paolo!
---
<p>Hope everyone has been getting into the 2013 swing of things! I know with a few days of out of office I had a chance to catch up on a bunch of reading. Some of these really filtered up to the top and I thought I would shoot off a really quick post on a few things I've tweeted about lately, or, at least flagged recently for personal digestion.. </p>
<p><a href="http://phenoelit.org/blog/archives/2012/12/21/let_me_github_that_for_you/index.html">Hijacking Ruby on Rails apps through exposed "secret" tokens .. or Let Me Github That For You</a> - An analysis on the insecure handling of the secret_token.rb file present within Ruby (Rails) apps. As this is the secret key that's subsequently used for other secret key generation it should not, naturally, be committed into your GitHub repo. In Rails apps, 'rake secret' can help generate a new random string for population into your secret_token.rb file.</p>
<p><a href="http://armoredcode.com/blog/codesake-engine-and-two-weeks-of-bdd-development/">Codesake</a> - A quickly (and extensible) static analysis tool, or, at least the beginnings of one. I took a moment to skim <a href="https://twitter.com/thesp0nge">Paolo's</a> code the other day and it looks like this could potentially grow into something quite powerful. Not yet a <a href="http://brakemanscanner.org/">Brakeman</a> replacement, but, definitely something to keep an eye on.</p>
<p><a href="http://blog.diniscruz.com/2012/12/i-never-liked-term-rugged-software-what.html">I Never Liked The Term Rugged Software</a> - If you have trouble keeping up with all of <a href="https://twitter.com/diniscruz">Dinis'</a> content I can't really blame you, he posts a LOT, and, quite often to a depth that I struggle with. Regardless, this short and sweet post from him sort of stuck with me for a few days, and whilst I sort of like the idea of <a href="http://www.ruggedsoftware.org/">Rugged Software</a>, it more often makes me think of beards as opposed to resiliency.. Maybe Dinis is onto something!</p>
<p><a href="http://intellavis.com/blog/?p=560">Continuous Integration Security Testing</a> - <a href="https://twitter.com/pubal">Jason</a> over at Intellavis performed a quick review of a few web security tools which could be run in automated fashions to assist with continuous integration. I don't really know if I agree with his conclusion (although, I do really enjoy w3af), I do think that more people should be doing this sort of work. If you're working on a security tool and aren't enhancing or exposing APIs or thinking about more flexible use-cases, you're doing it wrong.</p>
<p><a href="http://arstechnica.com/apple/2012/12/the-legacy-of-next-lives-on-in-os-x/">The Legacy of NeXT Lives on in OSX</a> - saw this tweet from <a href="https://twitter.com/merbist">@merbist</a> (RTd from someone I can't recall). Anyway, his tweet couldn't summarise this article better: "<em>Extremely well written article explaining Apple's underlying architecture for iOS/OS X strongly recommended.</em>"</p>
<p><a href="http://youtu.be/Wl5OQz0Ko8c">Jacob Appelbaum's #29c3 Keynote</a> - I started watching this on the TV at home, and even got the wife into it. Really insightful presentation and certainly had me thinking and reflecting on my involvement with open source software.</p>
<p><a href="http://www.warrenellis.com/?p=14548">Warren Ellis on Conservative Characters, Cyberpunk and Women who write SF</a> - <a href="https://twitter.com/warrenellis">Warren</a>, who is easily my favourite author of the past few years, posted this really quick Q&A on his blog. Having just released his latest novel, Gun Machine (which I promptly Kindled and smashed a good 10% in the first sitting), Warren's list of authors and other books gave me a future reading list I'll have to get started at some point. Also, if you haven't had a chance to read Crooked Little Vein get it. Whilst pretty short, I haven't enjoyed reading a novel as much as this since I read (and understood) Neuromancer (not that Crooked Little Vein is in anyway a SF/Cyberpunk novel).</p>
