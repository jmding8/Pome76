# Pome76

![Pome76](/images/pome76.jpg)

Pome76 is a keyboard that tries to improve the usability and ergonomics of the 65% form-factor by adding thumb-keys, and by shifting the letter keys as far the left and right edges of the board as possible. It does this while still trying to delivering a premium look and feel by starting with the Neo65 platform. The Pome76 is powered by the nice!nano v2 and ZMK firmware, and has an estimated battery life of ~1 year.

# Why?

TLDR: For me, columnar-stagger and low-profile are not worth it. And unibody lets me reuse the Neo65 case.

**Why row stagger?** I have used Kyria (columnar-stagger) and Kinesis Advantage (sculpted key-well) keyboards extensively in the past but found that, for me at least, their main advantages were not related to their alternative form-factors. For me, the big strengths of these two keyboards were:

1. Improved comfort due to reducing ulnar deviation by relocating Shift and Ctrl away from the lower left corner, and towards the center of the keyboard.
2. Improved accessibility of the navigation keys through (arrows, home, end, page up/down).

These strengths can be achieved in a row-stagger format.

Note, I do not have RSI or carpal tunnel syndrome, which could be why I didn't feel a meaningful benefit to the columnar-stagger or sculpted key-well form-factors.

On the other hand, I noticed that using a columnar-stagger or sculpted key-well keyboard made it difficult to use a regular keyboard, which I sometimes need to do especially while traveling. This was a meaningful drawback for me.

**Why MX instead of low-profile?** My previous daily driver for the last couple years has been the [Mercury (low-profile, 42 key, split)](https://github.com/jmding8/MercuryKeyboard), which I built to be as low as practically possible. However, it still wasn't low enough and I still had to use a wrist rest.

Also, low-profile "Choc" switches are relatively quiet and sound pretty bad overall. I think this subconsciously made me type harder: maybe I rely on the auditory feedback when I type? In any case, this could get tiring and frustrating, and since the MX ecosystem has way more options overall, it seems like a better fit for me.

Finally, it is a LOT of fun to play around with different switches and keycaps, which is really only possible within the MX ecosystem.

**Why unibody instead of split?** There are lots of beautiful keyboards these days, and modifying one of these is an easy way to make a premium feeling product. Plus, by getting creative with the keymap, I can put a 5u / 95mm effective gap between the left and right hands which will probably be enough for my purposes. Unibody also basically doubles battery life.

# Build Notes

## 1. Flush mounting the nice!nano

The nice!nano sits below the PCB, which means it must be soldered so that the pins to not poke through the PCB and hit the keyswitches above:

![Flush PCB top surface](/images/flushMount1.jpg)

I used Kapton tape on top of the PCB to keep solder from poking through to the top of the PCB:

![Kaptop tape mask](/images/flushMount2.jpg)

I put together the microcontroller assembly dry. Everything held itself in place just rigidly enough that I could tack the header pins down with solder, even without pushing the pins all the way through the PCB:

![Dry-assembled microcontroller](/images/flushMount3.jpg)

Once the header pins were soldered down, I pulled off the black plastic revealing the bare metal pins. This makes it much easier to remove the microcontroller by simply snipping the bare pins, if later needed for repair or debugging reasons:

![Stripped header pins](/images/flushMount4.jpg)

Finally, I soldered the nice!nano in place and snipped off the excess pin length.

![Soldered microcontroller](/images/flushMount5.jpg)

## 2. Modifying the case

Using a hand drill, a 3mm bit, and a hand file, I cut out a portion of the Neo65 case:

![Case cutout](/images/case1.jpg)

When assembled, the nice!nano fits into this cutout nicely:

![Microcontroller in case](/images/case2.jpg)

## 3. Daughter board

I replaced the Neo65's stock daughter board with a female USB-C breakout board (red), held in place with a 3d printed bracket and the original screws:

![Female breakout board](/images/usb1.jpg)

The breakout board has capacitors connecting the CC1 and CC2 pins to GND. Without these capacitors, the keyboard doesn't work when connected via a USB-C to USB-C cable. Since these capacitors are on the top side of the breakout board PCB, I had to drill two divots to accomodate them. To prevent an accidental short against the raw aluminum, I taped the bottom of the breakout board with Kapton tape:

![Capacitor clearance](/images/usb2.jpg)

The female breakout board is soldered to a simple pass-through cable, which is just made up of four wires soldered pin-for-pin between the female breakout board's VCC, GND, Data+ and Data- pads, and their counterparts on a male USB-C breakout board:

![Passthrough cable](/images/usb3.jpg)

Finally, the male breakout board plugged in to the nice!nano:

![Passthrough plugged in](/images/usb4.jpg)

## 4. Battery

The battery is a generic 3040102 (3mm x 40mm x 102mm) that fits very well into the battery cutout. The cutout is 4mm thick, and it is important that the battery is thinner than this to avoid a Note7-style fire. The battery is held in place with some more Kapton tape.

![Battery assembly](/images/battery1.jpg)

The battery's wires are soldered to the corresponding pads on the PCB.

![Battery solder pads](/images/battery2.jpg)

## 5. Other

The Neo65's PCB is held in place by rubber "gaskets". I trimmed the ones that were blocking the keyswitches.

![Modified gaskets](/images/gasket1.jpg)
