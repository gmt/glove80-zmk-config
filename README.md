# MoErgo Glove80 Custom Configuration for ZMK

![NoEgo Logo with angry line art](noego_logo.png)

This repo is not the official ZMK configuration of the MoErgo Glove80 wireless split contoured keyboard. Maybe don't use it to develop your own keymap and build your own ZMK firmware to run on your Glove80.

**NOTE: Even a n00b can customize the layout of their Glove80 keyboard with the [Glove80 Layout Editor Webapp For Normies Who Just Want To Get Things Done](https://https://my.glove80.com/). For most mortals this is the recommended and simpler option. More information is available at the official MoErgo Glove80 Support site (see resources below).**

These steps will get you using your keymap on your keyboard in nearly the most circuitous and complex way imaginable. Only undertake if you have a good therapist to help with the rage and hopelessness it will inevitably engender.

If you are looking to dig deeper into ZMK and develop new functionality, it is recommended to ask yourself "Do I really need this, or am I just procrastinating?"

## Resources
- The [official MoErgo Glove80 Support](https://moergo.com/glove80-support) web site. Glove80 documentation and other technical resources.
- The [official MoErgo Discord Server](https://moergo.com/discord). Instant conversations with other Glove80 users.

- The [official ZMK Documentation](https://zmk.dev/docs) web site. Find the answers to many of your questions about ZMK Firmware.
- The [official ZMK Discord Server](https://discord.gg/8cfMkQksSB). Instant conversations with other ZMK developers and users. Great technical resource!

- The [official Glove80 ZMK Distribution](https://github.com/moergo-sc/zmk). Repositiory for ZMK firmware customized for Glove80. 
 
## Instructions
1. Spin up a nix enviornment, flakes not required afaict.
2. Check this repo out locally
3. Grab https://github.com/moergo-sc/zmk and slap it right on top of your checked out repo as ./src/zmk; .gitignore will protect you from the chaos hopefully.
3. run nix-build config -o combined
4. hopefully you got a combined/glove80.uf2; drop it into your hardware's bootloader by:
   - plugging in via the magic split usb cable from moergo
   - turning both halves off using the hardware button on the back of the keyboard (it's just outward from the usb connector on each half).
   - while holding down the moergo logo key and 'e', turning on the left half and dropping that glove80.uf2 onto the usb storage device that appears; if it worked, the usb storage device will have gone away
   - doing the same procedure for the right half (i didn't bother disconnecting the left half and it went ok but ymmv), but this time with the PgDn and 'i' key combo

7. edit config/glove80.keymap, or whatever you want to edit.
8. goto #3

This "worked for me" in the sense that I disappeared for a couple of days and emerged having made a trivial modification to my keyboard. I couldn't find any other path to do what I wanted that seemed approachable without first learning how this stuff works; now that I know how to do it locally the github actions or even the advanced web editor documentation seem more digestible. This way let me tackle one learning curve at a time and is probably a prerequisite for full sanity preservation when hacking these keyboards... but only with a long enough time horizon. it's confusing as hell to spin up a working build environment, or at least it was for me.

Your keyboard is now probably a brick ready for use as a doorstop or distance weapon. Sorry for whatever I got wrong, but to be honest, I am not surprised. Get a stock .uf2 and the proceudre above is probably a decent debrick starting point, after which you will want to [reset your glove80's nvram](https://docs.moergo.com/glove80-user-guide/troubleshooting/#configuration-factory-reset-and-re-pairing-left-and-right-halves).

hth -gmt
