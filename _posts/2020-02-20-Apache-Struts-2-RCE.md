---
layout: post
section-type: post
title: Apache-Struts-2-RCE
category: web-application-security
tags: [ 'bugbounty', 'appsec' ]
---

**DIGEST**

Apache Struts is a framework that uses java. It can help to develop web applications. In Apache Struts RCE, A vulnerable application is not properly validating the malicious HTTP request which contains IGNL expression (Crafted Malicious payload). A successful attack can lead to Remote code execution.

**CVE-ID:** CVE-2017-5638

**CVSS Vector**

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H

**Disclaimer**

All my posts are focused only to educate people from my experience. It will not contain stories about how I did ;) May have a path to learn!!

**Key points**

1. Use Wapplayzer
