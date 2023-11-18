# Pome76

![Pome76](/images/pome76.jpg)

Pome76 is a keyboard that attempts to strike a personal balance between productivity, ergonomics, aesthetics, and cost. It starts as a Neo65 and adds a custom PCB powered by a nice!nano v2 and ZMK firmware. It is designed around an unconventional keymap which pushes the home positions as far towards the left and right edges of the board board as possible (note the position of the F and J keys).

If you are interested in one, let me know as I still have 3 leftover PCBs.

# Keymap

The keymap is a big part of this board's concept. For the below keymap, blue = left, red = right, and white = infrequently used.

![Keymap](/images/keymap.jpg)

In addition, there are the following combos:

1. `SD` = Shift
1. `DF` = Numbers layer
1. `XC` = Shift layer
1. `CF` = F-keys layer
1. `KL` = Shift
1. `RG` = Tab
1. `FG` = Esc
1. `JK` = Quote
1. `,.` = Forward slash
1. `HU` = Menu
1. `NM` = Caps Lock
1. `HU` = Menu

Some of the ideas involved with this keymap:

* Dividing roles means every key + modifier combination is accessible, even weird ones like Ctrl + Shift + F5.
  * Left fingers control layers
  * Right fingers control layered keys
  * Left thumb controls modifiers
* The two hands are pushed as far to the left and right edges of the keyboard as possible. The keys in between are relatively unused.
* Using combos with tight timeouts (35ms) to control modifiers and layers makes it possible to put them on the home row, with basically zero accidental activations even when rolling keys.
* Putting combos on keys that are typically controlled by one finger (e.g. `RG` = Tab) permits the use of a very loose timeout (200ms).


# Why?

TLDR: For me, columnar-stagger and low-profile are not worth the drawbacks. And unibody lets me reuse the Neo65 case while still having a 95mm gap between hands.

**Why row stagger?** I have used a Kyria (columnar-stagger) and a Kinesis Advantage (sculpted key-well) extensively in the past but found that for me, the main advantage of these keyboards is not due to the non-standard physical layout. For me at least, their big strengths are:

1. Improved comfort due to relocating the Shift and Ctrl keys away from the lower left corner, towards the center of the board (i.e. reduced ulnar deviation).
2. Improved accessibility of the navigation keys through the use of layers (arrows, home, end, page up/down).

These are features we can have in a row-stagger format.

I also noticed that using a columnar-stagger or sculpted key-well board makes it difficult for me to go back to a regular keyboard. Since I am sometimes forced to do this (while traveling for example), it is a meaningful drawback for me. On balance, migrating away from row-staggered layouts just isn't worth it for me. 

Note, I do not have RSI or carpal tunnel syndrome, which may be part of why I don't find columnar-stagger or sculpted key-wells worth it.

**Why MX instead of low-profile?** My previous daily driver for the last couple years has been the [Mercury (low-profile, 42 key, split)](https://github.com/jmding8/MercuryKeyboard) which is designed to be as low as practically possible. However it still isn't low enough and I still have to use a wrist rest.

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
