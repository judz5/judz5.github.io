---
layout: post
title:  "Cheap Yellow Marauder"
date:   2024-04-16
categories: Cybersecurity
---

Hi!
Once again, Reddit has provided me with another great hacking tool. This time for the low price of $20.

## The Cheap Yellow Display

Meet the Cheap Yellow Display ([ESP32-2432S028R](https://www.amazon.com/dp/B0BVFXR313?psc=1&ref=ppx_yo2ov_dt_b_product_details)). This $20 board features an ESP32 (Wifi __and__ bluetooth!), 320x240 LCD touchscreen display, an SD card slot, and a USB for both power and data transfer. If you want to skip the middleman you could even snag it for as low as [$5](https://www.aliexpress.us/item/3256804514312344.html?spm=a2g0o.productlist.main.3.7a2413726Tfeuq&algo_pvid=02b9fc0d-fe15-4ccc-b8db-9a83bd84f4c9&algo_exp_id=02b9fc0d-fe15-4ccc-b8db-9a83bd84f4c9-1&pdp_npi=4%40dis%21USD%2116.25%215.64%21%21%2116.25%215.64%21%402103201917119890498976079e579f%2112000030150215365%21sea%21US%210%21AB&curPageLogUid=Unb8iLsn9jd5&utparam-url=scene%3Asearch%7Cquery_from%3A). Thanks to "[Witnessmenow](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display)" on github, there is a ton of great information on how to work with this display.

It only took me about a minute from finding it, to having two on the way to my house. I've got alot of ideas for projects with this little board, but today i want to discuss the [ESP32 Marauder](https://github.com/justcallmekoko/ESP32Marauder) port for it.

## ESP32 Marauder

The ESP32 Marauder is "a suite of WiFi/Bluetooth offensive and defensive tools for the ESP32". It was developed by [justcallmekoko](https://github.com/justcallmekoko/), who has a much beefier version available [for sale](https://www.tindie.com/products/justcallmekoko/esp32-marauder/). 

Just to name a few features, the marauder features Wifi sniffing, deauth attacks, beacon spamming, Bluetooth spamming, and more. For $20 how could you pass this up? 

Flashing the display with the Maraduer is possibly one of the easiest things I have ever done. Thanks to [Fr4nkFletcher](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display) on github, who developed a easy to use webflasher. All you need to do is plug it in, select your device, and click flash. You do need to setup your arduino libraries first, but if you've read this far, I assume you know how to follow a [guide](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY).

## Hows it work?

I dont know (*yet*)! I'll update this post later once I figure it out, I just wanted to share this device. I'll have to do some more learning about wifi protocols and get back to yall.
