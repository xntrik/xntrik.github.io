---
layout: post
status: publish
published: true
title: SAMM Self Assessment Tool
permalink: samm-self-assessment-tool
author:
  display_name: Christian
  login: xntrik
  email: xntrik@un-excogitate.org
  url: ''
author_login: xntrik
author_email: xntrik@un-excogitate.org
wordpress_id: 798
wordpress_url: http://un-excogitate.org/?p=798
date: '2013-10-24 10:00:06 +0000'
date_gmt: '2013-10-24 02:00:06 +0000'
tags:
- owasp
- web application
- work
- Security
- ruby
- development
- amazon
comments: []
---
<p>This is primarily a reblog from our Asterisk Labs post here: <a href="http://labs.asteriskinfosec.com.au/samm-self-assessment-tool/">http://labs.asteriskinfosec.com.au/samm-self-assessment-tool/</a>.</p>
<p>Over a year ago I wanted to have more of a play with Rails and jQuery, at the same time, I was also interested in providing a really quick way for people and organisations to perform a lightweight <a href="http://www.opensamm.org">OpenSAMM</a> self-assessment. And so SSA was created.</p>
<p>--Original Post--</p>
<p>Asterisk are happy to be releasing their first public beta of the <a href="https://ssa.asteriskinfosec.com.au/">SAMM Self Assessment Tool</a>, or SSA. One of our favourite <a href="https://www.owasp.org/index.php/Main_Page">OWASP</a> projects is the <a href="http://www.opensamm.org/">OpenSAMM</a> project, and for those who haven't seen OpenSAMM before, it is a framework to help organisations to evaluate their current software security practices, and build measurable targets and plans for improving these practices.</p>
<p>Part of OpenSAMM includes conducting assessments (you can't manage what you can't measure right?). The OpenSAMM methodology categorises these assessments as either Lightweight or Detailed. SSA aims to provide a very simple way to perform this Lightweight assessment, and compare your current status with some pre-canned target states. And literally, that's it.</p>
<p>We've used this tool on a number of engagements to quickly gauge where an organisation is, and it's certainly helped with figuring out the 'current state' of an organisations software security maturity.</p>
<p>There's currently two different ways you can use SSA:</p>
<ol>
<li>You can visit <a href="https://ssa.asteriskinfosec.com.au/">https://ssa.asteriskinfosec.com.au/</a> and complete the checklist directly. You don't even have to save your assessment anywhere if you don't want. On the other hand, if you want to store your results, there's a few ways to do that, such as in your cookies or online in a database. For online storage you need to Sign Up, either with a username and password (please don't re-use your passwords folks), or you can sign in with a Google account too.</li>
<li><a href="https://github.com/AsteriskLabs/ssa">Clone</a> a copy of the Rails app and spin it up somewhere locally. We recognised quite early on that some organisations may feel uncomfortable with tracking this sort of information on the Internet, so, if you have the capability, sure, feel free to clone the repository locally and do what you wish.</li>
</ol>
<p>SSA is being released under an MIT license, and our intent is to give it back to the OWASP community for further enhancements. We have a high level list of proposed features available on the <a href="https://github.com/AsteriskLabs/ssa/issues">GitHub page</a>, but currently they're being developed on a 'When Christian Has Time and is Sober' timescale. SSA forms part of our <a href="http://asterisklabs.github.io/">Toolkit</a>, of which we're slowly publishing other tools and utilities too. So watch this space!</p>
<p>As always, we're really interested in your feedback, queries, concerns, issues. So feel free to send us queries via <a href="https://twitter.com/asteriskinfosec">@asteriskinfosec</a> or as <a href="https://github.com/AsteriskLabs/ssa/issues">Issues</a> on the GitHub project.</p>
