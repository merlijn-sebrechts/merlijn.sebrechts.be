---
title: "Tutorial: S4A on Ubuntu"
layout: post
date: 2020-02-23
type: "post"
---

[S4A](http://s4a.cat/), or Scratch for Arduino, is an app that you can use to program Arduino boards using Scratch. You can program robots and LED's without writing any code: all you need to do is drag and drop instructions in the visual programming environment.

![Upload succeeded](/img/2020/s4a/s4a-shot01.png)

## Step 1: Install Arduino IDE and S4A

The first step is to install Arduino and S4A from the Snap Store.

```bash
sudo snap install arduino s4a
```

After that, you need to give the user account on your computer access to USB devices. Only administrators and user in the `dialout` group have access to Arduino board connected over USB. Because of that, you will get a "Permission Denied" error when you try to upload a program. In order to give your user access, run the following command and **restart** your computer.

```bash
# Add the current user to the `dailout` group
sudo usermod -a -G dialout $USER
```

After this, you need to **restart your computer**.

## Step 2: Upload S4A firmware to Arduino board

The next step is to Flash the S4A firmware on your Arduino board. This is required so that S4A can connect to your board to run your apps on it. You need to install this firmware using the Arduino IDE.

1. Download [the S4A firmware from here](http://s4a.cat/downloads/S4AFirmware16.ino) and open it in the Arduino IDE.

   ![Open the S4A firmware in Arduino IDE](/img/2020/s4a/s4a-firmware.png)

2. Connect your arduino UNO board to your computer using USB.

   ![Connect Arduino board to computer](/img/2020/s4a/setup-board.jpg)

3. Upload the firmware to your arduino by clicking the right arrow at the top of the Arduino IDE. When the firmware is uploaded you'll see the text "Done Uploading." on the grey bar just below the code.

   ![Upload succeeded](/img/2020/s4a/upload-successful.png)

## Step 3: Use S4A

After the upload succeeds, you can open the S4A program and start programming your board!

## Frequently Asked Questions

### When I upload code to the Arduino, I get a "permission denied" error

When you get the following error, that means that the Arduino IDE is not allowed access to the Arduino board.

```
An error occurred while uploading the sketch
avrdude: ser_open(): can't open device "/dev/ttyUSB0": Permission denied
```

This means that either the IDE or your current user is not allowed access to the Arduino USB device. Make sure you execute the following commands _as the user which runs the IDE_.

```bash
# Give the current user access to the USB device.
sudo usermod -a -G dialout $USER
```

After this, **restart your computer** and try again.

> *Note: if the user which runs the IDE does not have `sudo` permissions, you can grant the user permissions from another account by running `sudo usermod -a -G dialout <username>` and replacing `<username>` to the name of the user running the Arduino IDE.*
