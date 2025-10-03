---
layout: post
title:  "Web-accessible Camera Dorking"
date:   2024-06-17
categories: Cybersecurity
---

Hi!

While working through a SANS Sec504 (*Hacker Tools, Techniques, Exploits, and Incident Handling*) course book for fun, I stumbled accross a cool bit of google dorking that sent me down a web-accessible camera rabbit hole.

### Google Dorking 🤓

The book started me off with this simple google dork, 

```
inurl:"ViewerFrame?Mode="
```

This just checks for a common url phrase used by panasonic cameras web applications. While this did give me lots of interesting cameras to look at, I was actually able to find a few other vulnerable camera types with other google dorks. Some interesting ones being,

```
VB Viewer inurl:/viewer/live/ja/live.html
intitle:"webcam 7" inurl:'/gallery.html'
intitle:"Yawcam" inurl:8081
```

Although, the first 'ViewerFrame?Mode=" seems to have the most promise. This book also got me looking into Shodan, which I know has applications for this. However, I have yet to deep dive and figure out how to query it. I'll have to look into it more.

### Findings 🔎

From the first google dork, I was able to uncover a lot of interesting cameras, the most notable being a panasonic camera in a computer store (*ironic*).

<img src="/img/panasonic_store.png" alt="Vulnerable Store" style="max-width=100%; height: auto;">

Interesting... 

From here, I noticed the IP address in the link. I wonder where this store is? Luckily I had just finished making a tool [GeoTrace](https://github.com/judz5/GeoTrace). Its just a traceroute tool that also uses IP geolocation apis to track where your packets are going. So I went ahead and threw the IP into that, and got this map.

<img src="/img/GeoTrace_map.png" alt="GeoTrace Map" style="max-width=100%; height: auto;">

So it appears the store is in florida. I went ahead and did some googling for computer stores in florida, and came across a location with these images posted.

<img src="/img/Computer_store.png" alt="Computer Store" style="max-width=100%; height: auto;">

*Target Acquired*. So I sent the store a message and let them know they should probably unplug/secure that device. Hopefully they'll check their email.

### Conclusion

While not hacking by any means, this was a cool bit of OSINT. I mean, all it took was a google search. Its shocking how easy it can be to find these cameras, and the places they can be. At the end of the day im just an interested student who likes exploring tech, but for a threat actor these cameras could be the entry point to attacking a business.  
