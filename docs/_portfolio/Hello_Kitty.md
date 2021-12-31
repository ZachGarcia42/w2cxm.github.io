---
title: Hello Kitty
subtitle: "Launch Date: Sunday, 10/06/2013. 3:00pm EST. East Hill Plaza, Ithaca, NY."
image: assets/img/balloon/hello_kitty.jpg

caption:
  title: Hello Kitty
  thumbnail: assets/img/balloon/hello_kitty.jpg
---

### Mission Objectives
* Lightweight payload.
* Beacon CW.
* Timed or Short Duration flight.
* Foxhunt retrieval.

### Technology
* Alinco DJ-C4T - 300mw transmitter on 70cm - 446.450
* Mylar balloons.
* Party Gas will provide adequate lift for this launch.
* [Atmel AVR ATtiny13](http://ww1.microchip.com/downloads/en/DeviceDoc/doc2535.pdf)
* 71J3430 n-Type MOSFET for activating PTT on the radio
* [Hamlin HE721C0510 reed relay for nichrome burn](https://www.littelfuse.com/~/media/electronics/datasheets/reed_relays/littelfuse_reed_relays_he700_datasheet.pdf.pdf?utm_source=hamlin.com&utm_medium=redirect&utm_content=datasheet&utm_campaign=hamlin-lf)
* (3) AA Energizer Ultimate Lithium batteries, in series, for radio and nichrome.
* (1) CR 2032 button battery for Tiny13 controller, PTT and Piezo Electric Buzzer.

### Balloon Design

#### Parachute Size

I ran a MATLAB simulation and came up with these results:

```
   __Input:__
   Cd(Coefficient of Drag):  0.75                 = 0.75
   Parachute Diameter:       12 [in]              = 0.305 [m]
   wind speed:               22 [ft/s]            = 6.7056 [m/s]     
```

```
   __Output:__
   vxfinal: 	               22 [ft/s]            = 6.7056 [m/s]
   vyfinal: 	               15.6022 [ft/s]       = 4.75 [m/s]
   Kinetic Energy at impact: 0.56477 [ft*lbf]     = 0.766 [J]
   Max Force:                0 [lbf] at 500 [ft]  = 0 N
```

Cornell Rocketry has light weight parachute that is 12[in] diameter.


![](assets/img/balloon/hello_kitty_2.gif)

#### Project Weight

| **Element**                                |           | **Weight**                                |
| ------------------------------------------ | ----------| ------------------------------------------|
| Mylar Balloon                              |           | 1g                                        |
| Parachute & rigging                        |           | 2g                                        |
| Nichrome and lead wire                     |           | 5g (est)                                  |
| Radio                                      |           | 35g (Case partially removed)              |
| AA Batteries                               |           | 37g                                       |
| CR2032 Battery                             |           | 3g                                        |
| Microcontroller board                      |           | 20g                                       |
| Waterproof packaging                       |           | 10g (est)                                 |
| **Total**                                  |           | **113g**                                  |

<br>

#### Electronics Design
![](assets/img/balloon/electronics_hello_kitty.jpg)
![](assets/img/balloon/electronics_hello_kitty_2.jpg)

#### Code Design
```
set_timer(1 hour);
while(true) {
  transmitter on;
  send_morse("W2CXM/BALLOON");
  send_tone(10);
  send_dead_air(10);
  transmitter off;
  sleep(30);
}
```

#### Testing
* Battery testing of the (3) AA Energizer Ultimate Lithium revealed that we were able to successfully transmit for 9-10 hours before the batteries lost sufficient power. This well exceeds our mission requirements - aka “Find it before dark”.
* [Youtube of controller board test](https://www.youtube.com/watch?v=CkXRHUpymAI)
* Testing with 6 pound test fishing line shows that an Estes rocket igniter will cut it very easily. Before the igniter even catches fire, in fact. Further, the igniter seems durable enough to support the 100g payload during heavy jostling. We will suspend the package from the igniter for this mission.

#### Final Cost Estimate

| **Element**                                |           | **Cost**                                  |
| ------------------------------------------ | --------- | ----------------------------------------- |
| Mylar Balloon(s) & gas                     |           | $15                                       |
| Parachute                                  |           | $5                                        |
| String                                     |           | $0                                        |
| Nichrome and lead wire                     |           | $6                                        |
| Radio                                      |           | $20                                       |
| Battery                                    |           | $20                                       |
| Microcontroller board & components         |           | $20                                       |
| Waterproof packaging                       |           | $0                                        |
| **Total**                                  |           | **$86**                                   |

<br>

#### Reference Links and Inspirations
* [Morse code on Amtel chip. Also, home brew transmitter.](https://swharden.com/blog/2010-07-14-high-altitude-balloon-transmitter/)
