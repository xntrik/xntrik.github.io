---
layout: post
status: publish
published: true
permalink: dormant-domination
title: Dormant DOMination
author:
  display_name: Christian
  login: xntrik
  email: xntrik@un-excogitate.org
  url: ''
author_login: xntrik
author_email: xntrik@un-excogitate.org
date: '2017-08-05 18:00:00 +0800'
date_gmt: '2017-08-05 18:00:00 +0800'
tags:
- work
- appsec
- beef
---
<h2 id="dormant-domination-introduction">Introduction</h2>
<p>In the midst of "<a href="https://twitter.com/xntrik/status/886750283702743041">trying to be creative</a>", I thought I should finally pull my finger out and catch up on some other stuff that I haven't had a chance to blog about. Especially as <a href="https://twitter.com/antisnatchor">Michele</a> has progressed from bugging me about pushing up this code, to simply ignoring me entirely (still love you dude :P). Not to mention that I presented this at BSidesSF months ago! I have to preface that like most of the code I write, it's fairly hacky, and there's certainly a few bits that aren't as complete as I'd like. And I'm constantly time-poor (nb: I really struggle to open the laptop outside of work these days), so the idea of maintaining this code makes me want to cry. With that said, here it goes.</p>
<p>The idea was simple enough. Why not adjust <a href="http://beefproject.com/">BeEF's</a> (beef from here on in because .. capitalization fatigue) <a href="https://github.com/beefproject/beef/wiki/Autorun-Rule-Engine">Autorun Rules Engine</a> (ARE) such that instead of just running a set of modules upon hook, how about we prepare some modules, and wait for the network-context of the browser to change, and <i>THEN</i> run some modules. Even better, how about we try and store the results of those modules locally until the browser returns back to the original context.</p>
<p>This scenario becomes particularly interesting in the context of different networks with altering risk profiles, such as a public network versus a corporate network, or even airgapped networks. From an attacker's perspective, these non-Internet-accessible networks are a juicy target. It's also these sorts of scenarios that really highlight the importance of addressing CSRF vulnerabilities, especially on internal networks.</p> 
<p>I've run into some networks where inline security appliances have halted the beef payload from downloading. Sure, bypassing these is not that difficult, such as using TLS, or obfuscating the JS payloads. But it's also in the face of these controls that the <code>dormant-forward</code> method really shines. Imagine hooking a browser whilst it's on a public wifi with no perimeter controls. That tab, if it remains open, will continue to run. If that computer then changes network to a more critical network, there's nothing preventing the already in-memory JS from continuing to run. Even though the SOP is great at preventing JS from interacting freely with other origins, the control doesn't prevent all information from returning to differing origins. We can still gather information based on whether cross-origin requests fail, how quickly they fail, and so on.</p>
<p>But, before we get into the specifics, for those that haven't spent time in beef lately feel free to check out a <a href="https://un-excogitate.org/presentations/CactusCon2016-wtfbrowser.pdf">presentation</a> I was lucky enough to present at <a href="http://www.cactuscon.com/talks2016/">CactusCon</a> last year for a quick refresher of WTF beef is..</p>
<h2 id="dormant-domination-are-history">The History of the Autorun Rules Engine</h2>
<p>To try and provide a bit of context of the ARE, we have to delve into the history of beef. Back in the dark ages (when beef was written in PHP), one of the standard features was the autorun configuration. It was simple; when a browser is hooked to beef, run a module. It took a while until the same feature reappeared in the ruby re-write of beef, but it exists. And it's as simple as updating either your global (or module-specific) <code>config.yaml</code> to ensure that in the module definition you have defined <code>autorun: true</code>. You can see this demonstrated over <a href="http://www.subliminalhacking.net/2013/01/03/how-to-autorun-modules-in-beef-browser-exploitation-framework/">here</a>.</p> 
<p>ARE is similar, but provides a lot more 'logic' around when modules run, and how to run multiple modules. The <a href="https://github.com/beefproject/beef/wiki/Autorun-Rule-Engine">wiki</a> provides a lot more context around ARE, and how to use it. But in short, modules can either be sequentially chained (i.e. they run one after the other) or nested-forward chained (i.e. each module depends on the previous module to have completed properly, and can take the output of the previous module too). The nested-forward example is perfect, in that, it first gathers the internal IP of the browser, then takes that and uses it to configure and run the internal network fingerprinting module.</p>
<p><script src="https://gist.github.com/xntrik/aac49e471732a416c5a4bb3e3f217e0a.js"></script></p>
<h2 id="dormant-domination-concepts">Dormant-forward Chain Mode</h2>
<p>The new <code>dormant-forward</code> chain mode has the following phases:
<ol><li><b>Setup</b></li>
<li><b>Monitor</b> for network changes</li>
<li><b>Run</b> arbitrary beef modules</li></ol></p>
<p>The <b>Setup</b> phase itself goes through two steps:
<ol><li>Gather information about the current network I'm on. This is a combination of the existing <a href="https://github.com/beefproject/beef/tree/master/modules/host/get_internal_ip_webrtc">Get Internal IP WebRTC</a> module, and a new beef service to allow a browser to gather information about its external network. Such as ASN, ISP etc.</li>
<li>Initiate timers to help detect when the network has changed, and prepare subsequent modules</li></ol></p>
<p>The <b>Monitor</b> phase is composed of methods that run when the browser's network connectivity appears to have changed. This includes checking things like:
<ul><li>Are we not offline or online?</li>
<li>Are we back on the original network or a new network?</li></ul>
If we're on a new network, then lets kick off the network detection methods and determine if we have queued modules to execute.</p>
<p>Once we've determined we're going to <b>run</b> new modules there are a few configurable options that modify how we execute the modules. This includes:
<ul><li>How stealthy do we want to be on the network? i.e. do we want to cache module results locally in the browser until we return to the original network, or do we want to just send the results straight out</li>
<li>What are we going to do when we return home? Are we going to just kill all the timers and network-change detection, or do we keep on going</li></ul>
The <em>stealthy</em> parameter directly ties back into wanting to minimize our presense to perimeter network detection devices. With this enabled, we could have a browser hooked, connect to an internal network. Gather information about that network. Wait for a public network, and then send the results back to beef. Any perimeter network detection may not even be aware that there WAS a hooked browser on the network.</p>
<h2 id="dormant-domination-the-setup">The Setup</h2>
<p>For our example scenario the setup is like this: Let's assume a mobile browser gets hooked to beef on a public network.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="QXPbx81"><a href="//imgur.com/QXPbx81">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p>The browser meets the ARE targeting and is sent the <code>dormant-forward</code> payload.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="ekiOrdj"><a href="//imgur.com/ekiOrdj">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p><em>.. some time passes ..</em>. The browser ends up on a different network.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="vFiiZXR"><a href="//imgur.com/vFiiZXR">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p>Beef modules are run against local subnets, based on the <b>new</b> internal IP of the browser. The modules include ping-sweep on a subset of the local subnet, and then a port scan against discovered hosts. Again, this port scan is only against a sub-set of ports.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="hlQ4sqe"><a href="//imgur.com/hlQ4sqe">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p>The browser does NOT send the results of these modules back to the beef server.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="fwQ8pdk"><a href="//imgur.com/fwQ8pdk">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p><em>.. some more time passes ..</em>. The browser returns back to the original network, and sends its cached module responses back to the beef server.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="9izCRhU"><a href="//imgur.com/9izCRhU">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p>Here is an example of the ARE JSON file:</p>
<p><script src="https://gist.github.com/xntrik/259801a298ae110bcdbd56e5f0fc89a5.js"></script></p>
<h2 id="dormant-domination-closing">Closing</h2>
<p>Overall I was happy with the proof of concept, especially highlighting risks of devices crossing network boundaries with malicious JS in-memory, in the DOM. There are some loose-ends and a few implementation details which may not make this capability immediately usable by everyone. The biggest issue discussed at Bsides was accurate detection of networks. There were some suggestions to adjust <em>when</em> to send module-data back to beef. For instance, instead of waiting for the original network, perhaps just wait for the network to change to <em>any</em> network, then send the data.</p>
<p>Another issue that needs a bit of work is the new <code>/aslookup</code> capability in beef. The fact this is currently served from beef, and is used to detect the network, may divulge the beef server to detection technology. The idea was to make this capability as small as possible and perhaps allow it to be quickly deployed to Heroku or AWS. This would provide another avenue of obfuscating the location of your beef server from network perimeter devices.</p>
<p>Currently the <code>dormant-forward</code> option can only run either 1 or 2 modules. The original <code>nested-forward</code> mode can run 1+n modules, but I haven't reimplemented the module insertion logic exactly the same, and have been trying to think of nicer ways to accomplish this with JS.</p>
<p>You can download the presentation from here: <a href="https://un-excogitate.org/presentations/bsidessf2017-dormantdomination.pdf">https://un-excogitate.org/presentations/bsidessf2017-dormantdomination.pdf</a> [PDF]</p>
<p>The demonstration video is here:</p>
<p><iframe width="560" height="315" src="https://www.youtube.com/embed/LG0FdueFtdE" frameborder="0" allowfullscreen></iframe></p>
<p>And a recording of my BSidesSF 2017 presentation is available here:</p>
<p><iframe width="560" height="315" src="https://www.youtube.com/embed/5a3DvvbVPGY" frameborder="0" allowfullscreen></iframe></p>

