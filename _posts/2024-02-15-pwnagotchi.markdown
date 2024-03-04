---
layout: post
title:  "WiFi Hacking with Silly Faces"
date:   2024-02-14 11:58:59 -0600
categories: WiFi_Security
---

## The Pwnagotchi
I first found out about the [pwnagotchi](https://pwnagotchi.ai/intro/) on the birthplace of all good ideas, Reddit.

The pwnagotchi is an opensource project that can be flashed onto a Raspberry Pi zero. It can be integrated with a waveshare e-ink display, or run headless.

*Whats it do?* The pwnagotchi eats WiFi. With A2C Based "AI" via bettercap, the pwnagotchi eats wifi handshakes and trains off its data to maximize the crackable wpa handshakes it captures. It does this either passively, or by sending deauthentication packets to users and capturing their handshakes as they reconnect.

The best part is it can be completely wireless with a PiSugar battery for travel, and even makes cute faces at you while it chows down on wifi packets.

![](/img/pwngrass.jpg)

## How Handshakes Work

Most networks run on WPA/WPA2 Wireless protocol. If I was a laptop, applying for a job at a WPA WiFi access point, the first thing I would have to do is shake the boss's hand 4 times. This is called the 4-way Handshake. While shaking my boss's hand I would exchange 4 packets with him, and in those packets there would be very secret information about our super secure password. Those packets are what the Pwnagotchi eats.

{:refdef: style="max-width: 60%"; items-align: center;}
![](/img/wpa.png)
{:refdef}

By sniffing these packets an attacker (pwnagotchi) can later dictionary/bruteforce attack the encrypted handshake and recover the original wifi key. In many cases an attacker would only need to capture 1 of these 4 packets. 



However, not all networks are created equal. In many business environments WPA-Enterprise is used (over WPA-Personal), in which case a key is created per user session. This makes the pwnagotchi useless for cracking passwords, but its still fun to watch it capture the handshakes.

## Cracking Handshakes

The pwnagotchi is very well integrated with plugins, so it's really easy to set up some helpful tools for trying to crack your captured handshakes. You can configure it to automatically upload handshakes to wpa-sec via an api key, or you can opt to use hashcat and crack them locally. Of course this is all luck or computing power and all it takes is a good password to render cracking useless.

So thats it, use good wifi passwords.

## Conclusion

This project is really cool and taught me alot about WiFi security protocols. It was a simple build, and has an active community coming out with new mods every day. I hope to 3D print a case for it soon, and perhaps do the 'slimagotchi' mod. 

Next post I'll talk about performing Deauth Attacks on the ESP32 Marauder flashed on a Cheap Yellow Display for $20. Also have an ALFA AWUS036ACS antenna and GPS module coming soon... prepare for wardriving setup post.

Later.



