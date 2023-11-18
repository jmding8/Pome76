# Pome76

![Pome76](/images/pome76.jpg)

Pome76 is a keyboard that tries to improve the usability and ergonomics of the 65% form-factor by adding thumb-keys, and by shifting the letter keys as far towards the left and right edges of the board as possible (note the position of the F and J keys). It does this while still trying to deliver a premium look and feel at a reasonable cost, by starting with the Neo65 platform. The Pome76 is powered by the nice!nano v2 and ZMK firmware, and has an estimated battery life of ~1 year.

If you are interested in one, let me know as I still have 3 leftover PCBs.

# Why?

TLDR: For me, columnar-stagger and low-profile are not worth it. And unibody lets me reuse the Neo65 case while still keeping a 95mm gap between hands.

**Why row stagger?** I have used a Kyria (columnar-stagger) and a Kinesis Advantage (sculpted key-well) extensively in the past but found that for me, their main advantages were not related to their form-factor. For me at least, their big strengths are:

1. Improved comfort due to relocating Shift and Ctrl away from the lower left corner, towards the center of the keyboard (reduced ulnar deviation).
2. Improved accessibility of the navigation keys through layers (arrows, home, end, page up/down).

These advantages can be had in a row-stagger format.

Note, I do not have RSI or carpal tunnel syndrome which could be why I don't feel a meaningful improvement from columnar-stagger or sculpted key-wells.

On the other hand, I noticed that using columnar-stagger or sculpted key-well keyboards made it difficult to go back to a regular keyboard. Since that is something I occasionally need to do, especially while traveling, it is a meaningful drawback for me.

**Why MX instead of low-profile?** My previous daily driver for the last couple years has been the [Mercury (low-profile, 42 key, split)](https://github.com/jmding8/MercuryKeyboard), which is designed to be as low as practically possible. However it still isn't low enough and I still have to use a wrist rest.

Also, low-profile "Choc" switches are relatively quiet and also sound pretty bad overall. I think this subconsciously encourages me to type with more force: maybe I rely on the auditory feedback? In any case this can get tiring and frustrating. Since the MX ecosystem is so much more developed overall, it is a much better platform for sound tuning.

Finally, it is a LOT of fun to play around with different switches and keycaps, and there are way more options within the MX ecosystem.

**Why unibody instead of split?** It's just a lot easier to get a premium feeling result by modifying an existing keyboard, than it is to design and manufacture a premium custom split. Plus, by getting creative with the keymap, I can still put a 5u / 95mm effective gap between my hands (see the position of the F and J keys). Unibody also basically doubles battery life.

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

The breakout board has capacitors connecting the CC1 and CC2 pins to GND. Without these capacitors, the keyboard doesn't work when connected via a USB-C to USB-C cable. Since these capacitors are on the top side of the breakout board PCB, I had to drill two divots to accommodate them. To prevent an accidental short against the raw aluminum, I taped the bottom of the breakout board with Kapton tape:

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
