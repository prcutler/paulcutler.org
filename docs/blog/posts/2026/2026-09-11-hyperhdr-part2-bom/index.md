---
title: HyperHDR Part 2 - Bill of Materials
author: Paul Cutler
type: post
date: 2026-09-11
categories:
  - movies
tags:
  - hyperhdr
  - movies
  - tv
---

Have you ever looked at a project in the Adafruit Learn Guide system and thought, "That's way too expensive for a project, but it looks cool". This is one of those projects. Though 2 items make up almost a third of the cost, it does add up. And I'm not including the Raspberry Pi 5 I just happened to have laying around not doing anything. But I was lucky and got an unexpected bonus at work, so here we go.

I've spent the better part of the week researching all of these parts. When I decide to do a project like this, I go down the rabbit hole and try to learn as much as I can. I'll have more on that when it comes time to talk about the LEDs.

The total cost, excluding the Raspberry Pi, comes in at around $350. (Gulp). The USB capture card ($100) and 2 strips of LEDs ($88) make up the bulk of the cost.

| **Item** | **Price** | **Notes** |
|:-:|:-:|:-:|
| [Pi5 power supply](https://www.amazon.com/s?k=pi5+power+supply) | $15 | I've had a Pi 5 for a couple years, but just powered it off USB-C. Need to fix that. |
| [USB capture card - UGREEN 4K@60Hz Video Capture Card](https://www.amazon.com/UGREEN-Ultra-Low-Streaming-Recording-Compatible/dp/B0D4LV836Z) | $100 | Recommended by the HyperHDR team, this makes up almost a third of the cost |
| [LEDs - 60 LED 5v - BTF-LIGHTING RGB+Cool White SK6812](https://www.amazon.com/BTF-LIGHTING-Individually-Addressable-Flexible-Waterproof/dp/B01N49DSC1) | $88 (2 × $44) | Of course I need roughly 6 meters and they come in 5 meter strips, so I'll need two. Again, almost a third of the total project cost. The RGBWs are recommended for the extra white channel, so choosing the Sk6812s over WS2812 Neopixels.|
| [300w BTF-Lighting Power supply](https://www.amazon.com/dp/B01D8FLZV6/?coliid=I29ZROWYJT4NN9&colid=TZRWREZEGB51&ref_=list_c_wl_lv_ov_lig_dp_it&th=1) | $33 | Beefy, should be more than enough. I'm worried about heat, but I'll mount it on the DIN rails below. |
| [Pinfox 6ft 16 Gauge 3 Prong Power Supply Cord Cable](https://www.amazon.com/Pinfox-Universal-Appliance-Replacement-Pigtail/dp/B06XRKXLVV) | $11 |  |
| [Adhesive Cable Clips - 60 PCS XHF 5/8" Clear Clips](https://www.amazon.com/XHF-Adhesive-Management-Organizer-Ethernet/dp/B0C7TNXZQS) | $7 | Going to go with these instead of sticking the LEDs right onto the back of the TV. |
| [3' HDMI cables](https://www.mycablemart.com/store/cart.php?m=product_detail&p=9618) | $18 (2 × $9) | Already bought, had to test the HDMI splitter. |
| [Power supply mount / DIN rails](https://www.amazon.com/s?k=din+rail+power+supply+mount) | $10 |  |
| [2 USB-C to USB-A cables - Hrbzo USB-C Cable 3-Pack](https://www.amazon.com/Charging-Compatible-Samsung-Galaxy-Devices-Black/dp/B0B4JGLTZW) | $7 | Can't believe I don't have a couple of these laying around. |
| [CORSAHD 4K@60Hz HDMI Splitter 1x2](https://www.amazon.com/dp/B0CLL5GQXT?ref=ppx_yo2ov_dt_b_fed_asin_title) | $30 | More on this in the next blog post. |
| [Adafruit rp2040 Scorpio](https://www.adafruit.com/product/5650) | $15 | Again, recommended by the HyperHDR team. |

Next: The HDMI splitter
