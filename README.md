# Pome76

![Pome76](/images/pome76.jpg)

Pome76 attempts to balance productivity, ergonomics, aesthetics, and cost. It is a Neo65 with a custom nice!nano based PCB, ZMK firmware, and an estimated battery life of 1 year. It is designed around an unusual keymap which pushes the home positions out to the edges of the board.

If you are interested in building one, I may have PCBs available. Gerber, BOM and position files [are located here](/files/).

# Keymap

Blue = left hand. Red = right hand. White = rarely used.

![Keymap](/images/keymap.png)

<details>
  <summary><b>Combos</b></summary>

1. `SD`, `XC`, or `KL` = Shift
1. `DF` = Numbers Layer (can be combined with `SD`, i.e. `SDF` = Shifted Numbers Layer)
1. `CV` = F-Keys Layer (can be combined with `XC`, i.e. `XCV` = Shifted F-Keys Layer)
1. `RG` = Tab
1. `FG` = Esc
1. `JK` = Quote
1. `,.` = Forward Slash
1. `NM` = Caps Lock
1. `HU` = Menu

</details>

<details>
  <summary><b>Core concepts</b></summary>

* Dividing roles allows access to weird key + modifier combinations (e.g. Ctrl + Shift + F5).
  * The left fingers control layer activation.
  * The right fingers control the layered keys.
  * The left thumb controls modifiers.
* The two hands are pushed as far towards the left and right edges of the keyboard as possible to mimic a split keyboard. The keys in between are rarely used.
* Using combos with tight timeouts (35ms) to control layers (and Shift) makes it possible to put them on the home row with basically zero accidental activations, even when rolling keys while typing quickly.
* Putting combos on keys that are typically controlled by one finger (i.e. `RG`), or keys that are very infrequently typed in sequence (i.e. `,.`) permits the use of a very loose timeouts (200ms).

</details>

<details>
  <summary><b>Other keymap details</b></summary>

There are many implementation details that contribute to a polished user experience. If you are interested to learn more, please reach out. For example:

* Aggressively using positional hold-tap in combination with tap-unless-interrupted really helps prevent accidental home-row modifier activation.
* The `SD` Shift and `DF` Numbers Layer combos are not actually implemented using ZMK's combo feature. They are implemented using layer-tap and macro functionality, which allows them to be combined. For example, `SD` = Shift, `DF` = Numbers Layer, and when used together `SDF` = Shifted Numbers Layer.

</details>

# Why these design choices?

TLDR: For me, columnar-stagger and low-profile are not worth the drawbacks. And unibody lets me reuse the Neo65 case while still having a 95mm gap between hands.

<details>
  <summary><b>Why row stagger?</b></summary>

I used columnar-staggered and sculpted key-well boards (Kyria and Advantage) pretty extensively in the past but found that they made it really hard to go back to a regular keyboard. Since I have to do this pretty often (especially while traveling), this is a pretty big drawback for me.

I also just never experienced a significant improvement in comfort or productivity from these new layouts. Although theoretically they should be better, it just didn't seem to translate into real world benefits for me. At the end of the day, I personally couldn't justify abandoning row-stagger.

For me, moving the Shifts to the home row (S+D and K+L combos) and the modifiers to the thumb cluster basically eliminated ulnar deviation, which seemed to clear up any (admittedly minor) pain I did have.

</details>

<details>
  <summary><b>Why MX instead of low-profile?</b></summary>

My previous daily driver for the last couple years has been the [Mercury (low-profile, 42 key, split)](https://github.com/jmding8/MercuryKeyboard) which is designed to be as low as practically possible. However it still isn't low enough and I still have to use a wrist rest.

Also, low-profile "Choc" switches are relatively quiet and also sound pretty bad overall. I think this subconsciously encourages me to type with more force: maybe I rely on the auditory feedback? In any case this can get tiring and frustrating. Since the MX ecosystem is so much more developed overall, it is a much better platform for sound tuning.

Finally, it is a LOT of fun to play around with different switches and keycaps, and there are way more options within the MX ecosystem.

</details>

<details>
  <summary><b>Why unibody instead of split?</b></summary>
  It's just a lot easier to get a premium feeling result by modifying an existing keyboard, than it is to design and manufacture a premium custom split. Plus, by getting creative with the keymap, I can still put a 5u / 95mm effective gap between my hands (see the position of the F and J keys). Unibody also basically doubles battery life.
</details>

# Build Notes

![Guts](/images/battery1.jpg)

<details>
  <summary><b>Flush mounting the nice!nano</b></summary>

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

</details>

<details>
  <summary><b>Modifying the case</b></summary>

Using a hand drill, a 3mm bit, and a hand file, I cut out a portion of the Neo65 case:

![Case cutout](/images/case1.jpg)

When assembled, the nice!nano fits into this cutout nicely:

![Microcontroller in case](/images/case2.jpg)

</details>

<details>
  <summary><b>USB daughter board</b></summary>

I replaced the Neo65's stock daughter board with a female USB-C breakout board (the red PCB, from Aliexpress), held in place with a 3d printed bracket and the original screws:

![Female breakout board](/images/usb1.jpg)

The breakout board has capacitors connecting the CC1 and CC2 pins to GND. Without these capacitors, the keyboard doesn't work when connected via a USB-C to USB-C cable. Since these capacitors are on the top side of the breakout board PCB, I had to drill two divots to accommodate them. To prevent an accidental short against the raw aluminum, I taped the bottom of the breakout board with Kapton tape:

![Capacitor clearance](/images/usb2.jpg)

The female breakout board is soldered to a simple pass-through cable, which is just made up of four wires soldered pin-for-pin between the female breakout board's VCC, GND, Data+ and Data- pads, and their counterparts on a male USB-C breakout board (from Aliexpress):

![Passthrough cable](/images/usb3.jpg)

Finally, the male breakout board plugged in to the nice!nano:

![Passthrough plugged in](/images/usb4.jpg)

</details>

<details>
  <summary><b>Battery</b></summary>

The battery is a generic 3040102 (3mm x 40mm x 102mm, from Aliexpress) that fits very well into the battery cutout. The cutout is 4mm thick, and it is important that the battery is thinner than this to avoid a Note7-style fire. The battery is held in place with some more Kapton tape.

![Battery assembly](/images/battery1.jpg)

The battery's wires are soldered to the corresponding pads on the PCB.

![Battery solder pads](/images/battery2.jpg)

</details>

<details>
  <summary><b>Gaskets</b></summary>

The Neo65's PCB is held in place by rubber "gaskets". I trimmed the ones that were blocking the keyswitches.

![Modified gaskets](/images/gasket1.jpg)

</details>
