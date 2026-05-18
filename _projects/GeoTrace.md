---
layout: post
title: GeoTrace
description: Geolocation Traceroute tool in Python
year: 2024
tags:
  - Python
  - Networking
---

     ▄▄ • ▄▄▄ .      ▄▄▄▄▄▄▄▄   ▄▄▄·  ▄▄· ▄▄▄ .
    ▐█ ▀ ▪▀▄.▀·▪     •██  ▀▄ █·▐█ ▀█ ▐█ ▌▪▀▄.▀·
    ▄█ ▀█▄▐▀▀▪▄ ▄█▀▄  ▐█.▪▐▀▀▄ ▄█▀▀█ ██ ▄▄▐▀▀▪▄
    ▐█▄▪▐█▐█▄▄▌▐█▌.▐▌ ▐█▌·▐█•█▌▐█ ▪▐▌▐███▌▐█▄▄▌
    ·▀▀▀▀  ▀▀▀  ▀█▄▀▪ ▀▀▀ .▀  ▀ ▀  ▀ ·▀▀▀  ▀▀▀ 


[GeoTrace](https://github.com/judz5/GeoTrace/tree/non-curses) is a Python traceroute tool with geolocation.

Uses UDP packets with TTL (Time to live) values to trace the route to a destination address. Location data is pulled from ip-api.com, and (*in progess*) visualized on a map. 

## Usage

  You can run the GeoTracer script to trace the route to a specified domain or IP address. For example:

```sh
python Trace.py
```

  the user is prompted for the target URL via ~~curses~~ cli. Traceroute output is printed, and a folium map is saved as 'traceMap.html' with a ping at each hopped location.

## Example Output

```sh
Tracing to 151.101.64.223
Hop #1: 192.168.1.1, City1, Region1, Country1
Hop #2: 10.0.0.1, City2, Region2, Country2
Hop #3: 203.0.113.1, City3, Region3, Country3
```

---

<img src="/img/GeoTrace_map.png" alt="GeoTrace Map" style="max-width=100%; height: auto;">
