---
layout: post
section-type: post
title: Apache-Struts-2-RCE
category: web-application-security
tags: [ 'bugbounty', 'appsec' ]
---

**DIGEST**

Apache Struts is a framework that uses java and It can help to develop web applications.
In Apache Struts RCE, A vulnerable application is not properly validating the malicious HTTP request which contains IGNL expression with Malicious payload). A successful attack can lead to Remote code execution.

**CVE-ID:** CVE-2017-5638

**CVSS Vector String:** CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H

**Disclaimer:**

All my posts are focused only to educate people from my own experience. It will not contain stories about how I did ;) May have a path to learn!!

**Root Cause:**

A Vulnerable Jakarta Multi parser in Apache struts is not properly validated the content-type header. So, the injected payload treated as an OGNL Expression and evaluated at the system level. An attacker can use this flaw to execute OGNL expressions that in turn execute system commands.

**Recon Ways:**
 <p style="text-align:left;">1. Wapplayzer addon may help you to find the framework and other library versions.</P>
 <p style="text-align:left;">2. Check the application page source and look for endpoints with the ".action" extension.</P>
 <p style="text-align:left;">3. Collect all the URLs using burp spider or other crawling tools. </P>
 <p style="text-align:left;">4. Craft your own Malicious OGNL payload and inject on "Content-Type". (refer below resources) </p>
 <p style="text-align:left;">5. Or Use this <a href="https://github.com/mazen160/struts-pwn">script</a> to automate the things. </p>

**POC Snapshot:**

![struts2](../../../../img/appsec/apache-struts-2-RCE.png)

**Resources:**

<https://www.synopsys.com/blogs/software-security/cve-2017-5638-apache-struts-vulnerability-explained/>

<https://medium.com/@abhishake100/rce-via-apache-struts2-still-out-there-b15ce205aa21>

<https://blog.lucideus.com/2017/12/exploiting-apache-struts2-cve-2017-5638.html>

<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5638>

<h5><center>All Credits to contributors and Thanks for reading ❤️! </center></h5>
<h5><center>Feel free to leave a comment 💬 below.</center></h5>
