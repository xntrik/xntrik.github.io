---
layout: post
status: publish
published: true
permalink: facebook-ios-clipboard
title: Facebook iOS App Scrapes Your Clipboard?
author:
  display_name: Christian
  login: xntrik
  email: xntrik@un-excogitate.org
  url: ''
author_login: xntrik
author_email: xntrik@un-excogitate.org
date: '2015-10-17 17:00:00 +0000'
date_gmt: '2015-10-17 17:00:00 +0000'
tags:
- Security
- development
---
<p>I <a href="https://twitter.com/xntrik/status/655250595473788929">noticed</a> yesterday that the Facebook iOS app appears to scrape your clipboard for URLs, offering to paste the URL into your next Facebook status update. You can see an example of this at the bottom of this post. I wasn't alone in thinking that this felt a little creepy, similar sentiment appears to have popped up on <a href="https://www.reddit.com/r/apple/comments/3p4qkl/further_conspiracy_facebook_app_accesses/">reddit</a>.</p>
<p>So what does this mean, and what can we do? Well, firstly, there isn't a permission to control access to the clipboard. The <a href="https://developer.apple.com/library/mac/documentation/Cocoa/Reference/ApplicationKit/Classes/NSPasteboard_Class/">NSPasteboard Class</a> is used to access the pasteboard server in AppKit used on OS X apps, while iOS uses the <a href="https://developer.apple.com/library/prerelease/ios/documentation/UIKit/Reference/UIPasteboard_Class/index.html">UIPasteboard Class</a>. In iOS, this class can be used to access the General pasteboard used for copy-cut-paste operations (and has existed since iOS 3.0). What this means is that any app has a means to access items in your clipboard. This itself is not as much of as a surprise compared to the likelihood that I've never seen this functionality used in such a creepy way before. Apparently Pocket and <a href="http://i.imgur.com/R4BC1NF.jpg">Chrome</a> have similar behaviors, just not that I've seen.</p>
<p>Why is it creepy? Well, for the App to know what is in the clipboard it has to pop the latest value, and determine if it's a URL or not. I did a few experiments and it didn't seem to scan beneath the item on top of the general clipboard. I.e. if I copied a URL, then copied a simple string, the feature wouldn't enable. In addition, after the app has extracted the URL, it doesn't often handle the same URL again, so the app itself may have an internal buffer. Data in the clipboard itself is either represented as an object (NSString, NSArray, NSURL etc) or a binary type. I'm assuming that mobile Chrome copies the selected URL as an NSString object as I used the text field select all and copy options, as opposed to the application's 'share' capability. If this is the case, then the Facebook app pops the top pasted object, and analyzes it (greps?) it to determine if it's a URL or not. Which means that the app is potentially accessing any strings in the clipboard.</p>
<p>URLs aren't the only thing I put in my clipboard. In fact, apart from URLs and other snippets of random content, other stuff I'm likely to copy and paste is content I can't remember, things like passwords (from a password management app) or one-time PINs. To assume that the Facebook app would do something malicious with this content is silly, but the fact that their app (and any other app) can access that content without user-interaction or permission is slightly unnerving.</p>
<p>So, should this feature be disabled? Perhaps. Should iOS have a permission ACL to limit which apps can arbitrary read the general pasteboard? Probably. Is this likely to occur anytime soon? I don't really think so. When I tweeted this, a few of the comments that came back included: use Facebook web instead; or, don't use Facebook you dick. Are these options I'm going to take. I don't really know. At least it's something to be mindful of. I can't imagine seeing this trend continuing without some kickback from privacy-minded people..so I guess we'll wait and see.</p>
<blockquote class="imgur-embed-pub" lang="en" data-id="jA9LW9F"><a href="//imgur.com/jA9LW9F">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>
