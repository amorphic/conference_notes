# Introducing kids to code through hardware using C++
## Sara Chipps

> While drag and drop interfaces are the rage, is there more value in teaching children real life coding? Come to this talk to learn about designing accessible APIs in C++ in a way that inspired kids to build and invent on their own.

* 9-14y girls rule the world
    * They know what's cool
    * They drive the revenue that drives much of the web
        * Instagram
        * Snapchat
    * But their futures are at risk
        * Computer literacy is a job requirement
        * 20-30% growth in dev roles in net 10 years
        * But
            * 18% of grad female
            * 15% of Googlers female
* Products for boys
    * Trained for youth to be Inventors, Creators, Architects of the future
    * Building, creating
* Product for pre-teen girls
    * All about consumption
        * Dolls that poop
        * Makeup
* People start coding young
    * Most of the room under 15
    * Most are boys
        * Gaming (map development, neopets etc)
    * Things that are fun without code but *can* be coded
        * Minecraft is fun without coding but a gateway
* Jewelbots
    * Social, programmable friendship bracelets
    * Actice online community
    * Send secret messages to their friends
    * Light up when friends are nearby
    * Extensible thru coding
        * Hold back the more advanced stuff that can only be unlocked with code
* Demo video
    * 8y old Clara
    * Live-coded Arduino C
    * "Now we're going to instantiate some classes..."
* Tech
    * 4 x RGB LEDs
    * Button
    * USB
    * nRF51822
        * 32bit ARM
        * 8 x simultaneous BT connections (central *and* peripheral)
        * Arduino
    * Needed to be small!
        * Limited storage
        * No space for compiler 
    * Platform
        * Cordova/Ionic
* Code
    * `nrf_drv_spi.h`
    * Not like software
        * Less Open Source
        * API for chip but not underlying hardware
        * No Stack Overflow
        * Some open-source hardware
            * Not viewed as "serious"
    * e.g. `nrf_drv_spi_transfer`
    * Functionality
        * Out of the box
            * Constant. Does not change.
        * Sandbox
            * 
    * Wrapped underlying 
        * E.g. LEDS
            * No pointers
            * LEDs use specific named colurs rather than hex etc
    `led,turn_on_single(SW, GREEN)`
        * Animations
            * Rainbow
            * Breathe
    * Ask community what they want next!
* Outcomes
    * Programmed to be a metronome
    * 44% Jewelbot users convert to coding
* Highway One
    * Hardware Accelerator
    * Talk to lots of kids
        * Exchange talks for friendship
        * Kids took idea from bracelet that matches clothes to friendship
* Lots of in-person events
    * People hit the first wall and many give up
* Don't store any information about kids ever

* Micropython?
* What about flashing firmware updates etc?
    * After community requests things
* How do you go about developing an arduino-centric product?
    * Circuit prototyping, manufacture
* Is installing/setting up Arduino IDE a challenge?
