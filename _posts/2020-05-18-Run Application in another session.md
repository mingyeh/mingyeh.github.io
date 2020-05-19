---
layout:     post
title:      Run application in another session?
subtitle:   Weird solution for weird problem
date:       2020-05-18
author:     Ming Yeh
header-img: img/home-bg-lamp.jpg
catalog: true
tags:
    - Session
---

## Begin of story

Well, I'm working on the change to a web application used to manage the configurations of trucks (like cabin, wheels, chassis, etc). After user finishes all the configuration steps, he or she is able to generate a report that contains all the configuration details and graphics with dimension info on it.

![Screen dump of report](https://mingyeh.github.io/img/tech_report.jpg "Screen dump of report")

The solution is based on Flash, which is way out of date. There is a Windows service hosted in application server used to handle the Flash-to-Image conversion. When user generates report, each graphic element in the report will send a message to message queue, and the Windows service will keep fetching messages from queue. Once a message is fetched from queue to Windows service, the service will invoke an external application that contains Flash component used to render the Flash, after the Flash is rendered successfully, a screen dump will be saved in png format, as the conversion result.

It used to be working well, until after some Windows or component update nothing returned from the external application but a black image.

Oooooooops!

