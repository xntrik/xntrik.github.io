---
layout: post
status: publish
published: true
title: Recent Readings on BeEF, MetasploiTor, Automation, SDLCs, Phishingggggggg
permalink: readings-beef-metasploit-automation-sdlc-phishing
author:
  display_name: Christian
  login: xntrik
  email: xntrik@un-excogitate.org
  url: ''
author_login: xntrik
author_email: xntrik@un-excogitate.org
wordpress_id: 762
wordpress_url: http://un-excogitate.org/?p=762
date: '2013-01-18 14:15:44 +0000'
date_gmt: '2013-01-18 06:15:44 +0000'
tags:
- phish
- browser
- Security
- beef
- development
- burp
- metasploit
comments:
- id: 99501
  author: tobias
  author_email: lordsaibat@gmail.com
  author_url: ''
  date: '2013-01-18 22:02:18 +0000'
  date_gmt: '2013-01-18 14:02:18 +0000'
  content: Send
---
<p>First off the bat is a couple of posts that I've had direct (some would say <em>intimate</em>) involvement.</p>
<p><a href="http://blog.beefproject.com/2013/01/beef-qr-fun.html">BeEF QR Fun</a> - Summarising some of the salient points from my OWASP AppSecAPAC 2012 presentation (<a href="http://www.slideshare.net/xntrik/shake-hooves-with-beef-owasp-appsec-apac-2012">Shake Hooves with BeEF</a>), I finally pulled my finger out and posted for the <a href="http://www.beefproject.com">BeEF</a> blog. Mainly focusing on custom mount points in BeEF with iFrame target-site impersonation, plus a dabbling of QR-codedness, the post hopes to demonstrate a few different methods to fit BeEF into your social engineering methodology.</p>
<p><a href="http://labs.asteriskinfosec.com.au/anonymous-post-compromise-control-via-tor-hidden-services/">Anonymous Post-Compromise Control via Tor Hidden Services</a> - My colleague <a href="https://twitter.com/dave_au">Dave</a> somehow managed to wrangle up an opus on utilising Tor to anonymise backdoor connectivity to compromised hosts over the Christmas period. Knowing Dave's relationship with beer I'm surprised that he still had the brain power to push this out (:P). If you have any interest in <a href="http://www.metasploit.com">Metasploit</a> and <a href="http://www.torproject.org">Tor</a> then you should check out his post.</p>
<p>And now onto other security stuff..</p>
<p><a href="https://air.mozilla.org/minion-automating-security-for-developers/">Minion - Automating Security for Developers</a> - There are a few different open source security automation projects going on at the moment (I mentioned Codesake <a href="http://un-excogitate.org/archives/2013/01/04/recent-readings-on-app-sec-ci-apples-os-freedom-and-cyberpunk/">recently</a>), but this one looks pretty interesting. It seems to be fairly modular (currently appears to interface with <a href="https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project">ZAP</a>, <a href="http://code.google.com/p/skipfish/">Skipfish</a> and <a href="https://github.com/mozilla/Garmr">Garmr</a>. The demo video seems really interesting, very point and click. For developers, this may be an ideal 'step' in their SDLC to catch bugs sooner.</p>
<p><a href="http://www.securitybistro.com/blog/?p=5024">Red October</a> - There's been quite a bit of noise about this attack recently. This was one of the first blog posts I read that seemed to provide a clear summary, with further links into the <a href="http://www.securelist.com/en/blog/785/The_Red_October_Campaign_An_Advanced_Cyber_Espionage_Network_Targeting_Diplomatic_and_Government_Agencies">Kaspersky reports</a>. This long-term campaign has apparently been targeting embassies and other governmental agencies (including defence) for the past 5 years.</p>
<p><a href="http://blog.securityps.com/2013/01/non-negotiable-elements-of-secure_15.html">Non-Negotiable Elements of a Secure Software Development Process: Part 2</a> - Nick Coblentz has been posting these great articles on elements of a secure systems or software development lifecycle which are non-negotiable. <a href="http://blog.securityps.com/2013/01/non-negotiable-elements-of-secure.html">Part 1</a> started with security requirements, while this post is focused on security architecture, configuration and other patterns. If you're working on embedding security into your development lifecycle definitely keep in the loop on Nick's posts.</p>
<p><a href="http://www.schneier.com/blog/archives/2013/01/man-in-the-midd_6.html">Man-in-the-Middle Attacks Against Browser Encryption</a> - Schneier recently posted a summary of how Nokia are intercepting HTTPS channels to offer better data transmission speeds over slower networks through compression and other means. This is really similar to a 2009 post of mine talking about how <a href="http://un-excogitate.org/archives/2009/04/04/the-risks-of-opera-mini/">Opera Mini</a> was doing the same thing.</p>
<p><a href="http://blog.spiderlabs.com/2013/01/defeating-aes-without-a-phd.html">Defeating AES Without a PhD</a> - <a href="https://twitter.com/dan_crowley">Dan Crowley</a> writes up an excellent post on leveraging some of Burp's more tricky intruder settings to understand (and attack) encrypted parameters within web apps. (Dan's a great guy, was happy to have a few beers with him while he was down in Sydney last year).</p>
<p><a href="http://blogs.rsa.com/laser-precision-phishing-are-you-on-the-bouncers-list-today/">Bouncer's Laser Precision Phishing</a> - RSA have posted an article on a particular phishing kit (i.e. pre-canned tool used to create or implement phishing sites) which utilises unique URL links for each recipient (so this kit includes the email/spam component too) to ensure that the site is only accessible (at least initially) by the victim. I'm sure there are ways to bypass this, but, it certainly may fool some simple phishing detection tools (such as used by finance or other sectors when they analysis abuse mailboxes or email bounce backs etc).</p>
<p>Okay, enough with the security stuff .. (Fine! .. here's one article..)</p>
<p><a href="http://www.int33h.com/test/mi/">Monkey Island Insult Swordfighter in your Browser</a> - for those fans of the original Monkey Island point and click adventure games you should check this out! This guy has dumped in browser form a collection of the sword-fighting challenges.. </p>
