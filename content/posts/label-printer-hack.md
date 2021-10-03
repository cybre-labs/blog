---
title: "Label Printer Modchip Hack"
date: 2021-09-17T15:00:51+01:00
tags: [modchip, hardware-hack, brother, p-touch]
description: "a modchip that adds wifi to the Brother P-Touch"
---

<video autoplay>
  <source src="solder-timelapse.mp4" type="video/mp4">
</video>

A year ago, in a Lidl, I pruchased a cheap Label printer. When revisiting the organization of the electronics small parts, the idea of adding wifi connection to the printer suddingly emerged. Normally, when you'd happen to hear the scentence "just add wifi" to a product not even designed for it, I would recommend to run away in sheer despair, but not this time! Adding Wifi to a cheap 20 Bucks Brother P-Touch printer is really worth the wrath.

![img](printer-front.JPG) ![img](flex-pcb.jpg)
_the Brother P-Touch_

![img](flex-pcb.jpg)

![img](schematic.png)

_The schematic:_
![img](printer-front.JPG)

_The pcb layout:_
![img](pcb.png)

![img](opened.JPG)

![img](solder-warning.JPG)

## Operation Breakdown

### Proof of work

### Example Code
```cpp
#include <Arduino.h>

void setup() {
  pinMode(D1, INPUT);
  pinMode(D2, OUTPUT); //Actually Output pin but INPUT as High-Z mode    
  digitalWrite(D2, HIGH);
}

void loop() {
  int k=0;
  while(true) {
    while(digitalRead(D1)!=LOW);
    digitalWrite(D2, LOW);
    delay(3.3);
    digitalWrite(D2, HIGH);
    k++;
    if(k>50) break;
  }
  delay(2000);
}
```

## PCB Design
The design goal for the PCB was to produce a board, that can be easily soldered on the P-Touch's board
with as little permanent changes as possible. That's acutally quite feasable as the ribbon cable between
the keyboard and the main board actually provides ground and 9V battery supply.

I ordered the flex PCB at [OSH Park](https://oshpark.com/). As usual, a few weeks later I had perfect ~~purble~~ flex PCBs with ENIG finish.

## Assembly

