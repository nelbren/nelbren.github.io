---
title: Nagios Check Status (NCS)
last_modified_at: 2018-05-11T23:22:00-06:00
ref: nagios-check-status
locale: en
categories:
- nagios
tags:
- github
- bash
- ncs
classes:
  - monitoring
excerpt: "Shows the server status and services monitored by nagios"
header:
  overlay_image: /assets/images/posts/mincs.png
  overlay_filter: 0.5
toc: true
toc_sticky: true
---

# Nagios Check Status (NCS)

> ![Nagios Check Status (NCS)](/assets/images/posts/nagios_check_status.png)

## What is it?
It is a set of scripts of [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) to obtain an exit report based on the server statuses and services monitored by [Nagios](http://www.nagios.org).

## How does it work?
It obtains the information from Nagios through the [MK Livestatus](http://mathias-kettner.com/check_mk.html) and process it to show the result in this way:

- **Screen saver:** changes the background color.
- **Alarm:** pronounces the status summary and/or plays an mp3 file.
- **Terminal:** shows a report by the demand.
- **Mail:** sends an email similar to the screen saver or terminal. 
- **Image:** generates an image, using a set of images as theme and a mark of time of color.


> Example of Images which update every 5 minutes:  
> Site #[01](https://npr3s.com/pelican/)   
> ![](https://npr3s.com/pelican/images/nagios/status_npro-vps-01.png)
> ![](https://npr3s.com/pelican/images/nagios/status_ndev-vps-01.png)  
> Site #[02](https://npr3s.net/pelican/)  
> ![](https://npr3s.net/pelican/images/nagios/status_npro-vps-01.png)
> ![](https://npr3s.net/pelican/images/nagios/status_ndev-vps-01.png)

> Example on how the screen saver displays: 
> ![NCS Protector de Pantalla Ejemplo](/assets/images/posts/ncs.png)

## Official site of [Nagios Check Status (NCS)](http://ncs.npr3s.com)
