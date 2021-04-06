---
title: X80 Adaptable AT Interface
seo:
  title: X80 Interface
  description: This is an adaptbale interface.
  extra:
    - name: 'og:type'
      value: website
      keyName: property
    - name: 'og:title'
      value: Welcome to Libris
      keyName: property
    - name: 'og:description'
      value: This is the documentation page
      keyName: property
    - name: 'twitter:card'
      value: summary
    - name: 'twitter:title'
      value: Welcome to Libris
    - name: 'twitter:description'
      value: This is the documentation page
layout: docs
---

X10 is an adaptable interface for assistive technology.

***

X80 is an Arduino-based multi-functional input/output device designed to be an interface between assistive technology inputs such as accessibility switches or specilist sensors and mainstream technology outputs, such as to a mobile phone or Augmentative and Alternative Communication (AAC) device.

An X80 can be preprogrammed and repurposed to perform a different function. It's built around the Adafruit Feather, generally the nrf82540 Express. It's essentially a Feather Wing for Assistive Technology (AT).

The PCB is still a work in progress but it is designed to have:

* Switch inputs via 3.5mm jack
* switch outputs via 3.5mm jack (simulates a switch press as an input into an Assistive Technology device)
* DB9 connector designed to accomodate devices meeting the TRACE SET Standard often used with accessibility input devices (https://park.org/Guests/Trace/pavilion/setdoc1.htm)
* buzzer
* potentiometer
* on/off switch

[View the GitHub Repository](https://github.com/AceCentre/X80)

## Setting up the Feather nrf82540

https://learn.adafruit.com/introducing-the-adafruit-nrf52840-feather

Before using the Feather, it's important to update the bootloader. Adafruit have detailed this, but I've put together all the files needed to upload the bootloader on Windows. If you'd prefer to use the latest files, refer to the Adafruit documentation. Files are available here:

https://acecentreuk.sharepoint.com/:f:/s/AnonymousShares/ElFAO-3ZVGpHiljoapMueEgBfhjUjkBUMkTm2YTfhzXXOg?e=cmfd61

Copy these files onto your computer. Open the command.tx files and change the Serial Port to the correct port. Copy and past the command into a command line promot. Hit enter. This should update the bootloader to version 0.4.1. The bootloader should be 0.2.9 or higher otherwise it will be unreliable under Windows when trying to upload files to the device using the Arduino IDE.

## Switch inputs

There is an issue with the switch inputs that need addressing. 

When a mono switch cable is inserted into the double switch port, it shorts two sections as returns a value of around 300 at the analog input pin. It shorts the Ring and the Tip. When a splitter cable is used, this short does not occur. The switch connected to the ring returns the 298. The tip gives around 230. This might be resolved by using a special cable with the connections wired in a different way. 

The circuit diagram shows a 4 way connector.

We're using a 4 pole connector so we should be able to wire this in a different way. https://uk.rs-online.com/web/p/jack-plugs-sockets/1248885/

## Standard Actions

## Switch Ports

The input and output switch ports are labelled 1 to 4 left to right.

Switch passthrough - switch input connected to switch inpout 4 and output 1

To simulate a switch press of output 2, use digitalWrite(SWITCH_OUTPUT_2,HIGH);   

To use the NeoPixel, there are some pre-defined colours. USe:

      pixels.setPixelColor(0, COLOUR_GREEN); // Moderately bright green color.
      pixels.show(); // This sends the updated

To use built in LEDs use

//digitalWrite(LED_BLUE, HIGH);

or digitalWrite(LED_RED, HIGH);







