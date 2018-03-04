---
layout: post
status: publish
published: true
permalink: advanced-protection
title: What was it like enabling Google Advanced Protection?
author:
  display_name: Christian
  login: xntrik
  email: xntrik@un-excogitate.org
  url: ''
author_login: xntrik
author_email: xntrik@un-excogitate.org
date: '2018-03-04 15:00:00 -0800'
date_gmt: '2018-03-04 15:00:00 -0800'
tags:
- Personal
- work
---
<p><em>tldr; Boring.. it was really boring.</em></p>
<p>It's the 27th of January, 2018. And yes, I've just signed into <a href="https://landing.google.com/advancedprotection/">Google's Advanced Protection</a>.. let's see how this goes.</p>
<p><em>Fast-forward to now.. March</em></p>
<p>I think the only hurdle was that apparently I had signed into YouTube on the TV. I don't even really remember doing that. Apart from that, this hadn't changed my usage of my gmail account (which I effectively live out of) at all. Oh, and the OS X native integration (which apparently I'd turned on to use the native calendar?) also stopped working.</p>
<p>I should probably provide some context. For those that don't know, Advanced Protection is an optional security configuration for your Google account that does a few things. First and foremost, it requires the use of hardware 2FA to sign in, no more SMS or Authenticator (aka: time-based one-time-pins) 2FA logins. The only reason I actually did this is because during the <a href="https://www.usenix.org/conference/enigma2018">Enigma conference</a>, Google were handing out these rad little kits which included the following:
<ol><li>Bluetooth, USB (with cable) and NFC dongle</li>
<li>USB-A, NFC dongle</li></ol></p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="a/InSWn"><a href="//imgur.com/InSWn"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p>So after having a chat with the mostly bored Google engineer behind the counter, I grabbed a kit and went on my way. A week or so later, I sat down with my devices and got cracking. Now, your mileage may vary, especially if you have old, or non-Google devices. My setup is fairly conducive to Advanced Protection, namely:
<ul><li><a href="https://store.google.com/product/pixel_2">Google Android Pixel 2</a> phone</li>
<li><a href="https://www.apple.com/shop/buy-mac/macbook-pro">MacBook Pro</a> (personal and work), running the Chrome browser</li>
<li>A Samsung ChromeBook (the same as from this great blog on the $169 development Chromebook <a href="https://blog.lessonslearned.org/building-a-more-secure-development-chromebook/">blog</a>)</li></ul></p>
<p>The other key controls that Advanced Protection enables include:
<ul><li>You can only sign in to Google services, like Gmail, Photos, and Drive, from Chrome OS or the Chrome Browser</li>
<li>Third party apps that want to access your Gmail or Drive will no longer work</li>
<li>iOS Apple Mail, Contacts and Calendar apps do not currently support hardware keys, and currently won't work</li>
<li>Restoring your account if you get locked out can take longer (apparently)</li></ul></p>
<p>The dongles themselves must adhere to the <a href="https://fidoalliance.org/specifications/overview/">FIDO Universal Second Factor (U2F) protocol</a>, but apart from that you can choose any, including those from Yubico. The two that came with the Google kit include the: <a href="http://a.co/ak2tEo6">Feitian MultiPass FIDO Security Key</a> and the <a href="http://a.co/gG2HwO8">YubiKey NEO</a> (or something very similar).</p>
<p>When Google first released (see <a href="https://www.blog.google/topics/safety-security/googles-strongest-security-those-who-need-it-most/">blog</a>) this feature it was primarily targeted at a small subset of users. Particularly those that they deemed at higher risk, such as campaign staffers, journalists, CEOs etc. I definitely don't fit into that demographic, but considering how much I depend on their services, the extra layer has been a great relief without any detrimental impact.</p>
<p>During the conference Google actually presented about the adoption of 2FA, and other facets of their authentication systems. I was somewhat surprised at how low their adoption was of 2FA (Less than 10% of active Google accounts use it). So, I expect that the number of people using Advanced Protection to be incredibly small. I'm also wondering of the other people that use it, how many have disabled it again, or whether their experience is similar to mine.</p>
<p><blockquote class="imgur-embed-pub" lang="en" data-id="a/mglV6"><a href="//imgur.com/mglV6"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script></p>
<p>Given some recent research by my good bud <a href="https://twitter.com/antisnatchor">@antisnatchor</a> on <a href="https://www.wired.com/story/chrome-yubikey-phishing-webusb/">Phishing YubiKeys</a> would I still recommend this? Sure, why not.</p>
<p>So, want to check it out? Buy yourself some keys and head over to <a href="https://landing.google.com/advancedprotection/">https://landing.google.com/advancedprotection/</a>.</p>
