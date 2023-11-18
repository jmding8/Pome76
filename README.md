# Pome76

![Pome76](/images/pome76.jpg)

Pome76 is a keyboard that attempts to improve over the usability of ~60% form-factor keyboards by adding thumb-keys, with a premium look, feel and sound. The case comes from a Neo65, which was modified to accept a PCB based on the nice!nano v2. It runs on ZMK firmware, and is wireless with an estimated battery life of ~1 year.

# Why?

TLDR: For me, columnar-stagger and low-profile are not worth it. And unibody lets me reuse beautiful keyboards.

**Why row stagger?** I used columnar-stagger (Kyria) and sculpted key-well (Kinesis Advantage) keyboards extensively in the past. However I found that, for me at least, the main ergonomic and productivity advantages of these keyboards came from:

1. Reduced ulnar deviation achieved by moving the Shift and Ctrl keys away from the lower left corner of the keyboard.
2. Improved accessibility of the navigation keys through the use of layers.

These two advantages are achievable with row-stagger keyboards. Furthermore, the columnar-stagger and sculpted key-well form-factors tended to make using a regular keyboard feel clumsy and frustrating. Given that I occasionally need to use regular keyboards, especially while traveling, this was a meaningful drawback.

**Why MX instead of low-profile?** My previous daily driver for the last couple years has been the [Mercury](https://github.com/jmding8/MercuryKeyboard), which I built to be as low as possible using commonly available parts. However, I still found that it wasn't low enough, and that I needed to use wrist rests anyway. Also, I found low-profile "Choc" switches' to sound really quiet and frankly terrible, which subconsciously made me type harder. Maybe I rely on the auditory feedback when I type? In any case, this got tiring and frustrating. And given that MX switch and keycap variety and availability is SO much better, the tradeoff just did not seem worth it to stick with low-profile.

I have to admit, it is a LOT of fun to play around with different switches and keycaps.

**Why unibody instead of split?** There are lots of beautiful keyboards these days, and modifying one of these is an easy way to make a premium feeling product. Plus, by tweaking the keymap, I can put a 5u / 95mm "virtual" gap between the left and right hands which will probably be enough.

Another minor advantage of unibody is that battery life is doubled.

# Build Notes

## 1. Flush mounting the nice!nano

The nice!nano sits below the PCB, which means it must be soldered so that the pins to not poke through the PCB and interfere with the keyswitches above:

![Flush PCB top surface](/images/flushMount1.jpg)

I used Kapton tape on top of the PCB to keep solder from building up on top of the PCB:

![Kaptop tape mask](/images/flushMount2.jpg)

I dry-assembled the microcontroller assembly with a spare ProMicro. Everything generally holds itself in place loosely, so that I can solder the header pins to the PCB in place from the top-side:

![Dry-assembled microcontroller](/images/flushMount3.jpg)

Once the header pins are soldered in place, I removed the black plastic, revealing the bare pins. This makes it much easier to remove the microcontroller by snipping the bare pins later, if it is necessary for repair or to fix a mistake:

![Stripped header pins](/images/flushMount4.jpg)

Finally, we can solder the nice!nano in place conventionally, and snip off the excess pin length.

![Soldered microcontroller](/images/flushMount5.jpg)

## 2. Modifying the case

Using a hand drill, a 3mm bit, and a hand file, I removed a portion of the Neo65 case:

![Case cutout](/images/case1.jpg)

When assembled, the nice!nano fits into this cutout:

![Microcontroller in case](/images/case2.jpg)

## 3. Daughter board

I replaced the Neo65's stock daughter board with a female USB-C breakout board, held in place with a 3d printed bracket and the original screws:

![Female breakout board](/images/usb1.jpg)

The female breakout board has capacitors connecting the CC1 and CC2 pins to GND. Without these capacitors, the keyboard doesn't work when connected via a USB-C to USB-C cable (neither data, nor power). These capacitors are on the top side of the PCB, so I had to drill these two divots to accomodate them. To prevent the raw aluminum from accidentally shorting something, I also wrapped the female breakout board with Kapton tape:

![Capacitor clearance](/images/usb2.jpg)

The female breakout board is soldered a four-wire straight pass-through cable, which is four wires, soldered pin-for-pin between the female breakout board's VCC, GND, Data+ and Data- pads, and their counterparts on a male USB-C breakout board:

![Passthrough cable](/images/usb3.jpg)

Finally, the male breakout board plugged in to the nice!nano:

![Passthrough plugged in](/images/usb4.jpg)

## 4. Battery

The battery is a generic 3040102 (3mm x 40mm x 102mm) that fits very well. The battery cutout is 4mm thick, and it is important that the battery is thinner than this to avoid a Samsung Galaxy Note 7 fire situation. The battery is held in place with some more Kapton tape.

![Battery assembly](/images/battery1.jpg)

The battery's wires are soldered to the corresponding pads on the PCB.

![Battery solder pads](/images/battery2.jpg)

## 5. Other

The Neo65's PCB is held in place by these rubber "gaskets". I had to cut some of them so they wouldn't conflict with the keyswitches.

![Modified gaskets](/images/gasket1.jpg)
