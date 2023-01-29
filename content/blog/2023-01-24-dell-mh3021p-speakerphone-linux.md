---
title: "Using Dell MH3021P speakerphone on Ubuntu Linux"
layout: post
type: "post"
date: 2023-01-24
categories:
  - 'Linux'
featured: "/2023/dell-mh3021p.jpg"
---

I recently bought the Dell MH3021P speakerphone. I want to use it for hybrid meetings and for recording audio during lectures. Dell doesn't say the device supports Linux, so I was curious to see how much of the device works. Google didn't have an answer so I bought the device to test it for myself.

Thankfully I can say all **the important parts work very well** out of the box on Ubuntu 22.04!

## What works on Linux

* Using the **speaker and microphone** from the device for calls. The audio is very clear and picks up everyone's voice when it's sitting in the middle of the table.
* Using the internal **USB-C docking station**. HDMI output, regular USB ports and USB-c ports all work as expected!
* **Charging** your laptop from the speakerphone. Connect your charger to the speakerphone, connect the speakerphone to your laptop and your laptop starts charging!
* The **volume buttons** on the speakerphone change the volume of my Ubuntu laptop (with GNOME).

## What does not work on Linux

* The **mute button** does nothing. I tried it with both Zoom and Microsoft Teams, and it doesn't seem to work. Moreover, it doesn't even mute its own microphone.
* The **"accept call" and "hangup"** button don't do anything either. I also tested this with Zoom and Microsoft Teams.

If you are interested in figuring out why these things don't work and how to get them to work, let me know in the comments or send me an email!

## Appendix: device logs and info

In case this is of interest or useful to anyone, these are some logs that give a bit more information about the internals of the device.

```log
$ lsusb
Bus 003 Device 014: ID 2109:8884 VIA Labs, Inc. Dell MH3021P           
Bus 003 Device 013: ID 413c:81e3 Dell Computer Corp. Dell MH3021P
Bus 003 Device 012: ID 2109:2822 VIA Labs, Inc. USB2.0 Hub             
Bus 002 Device 007: ID 2109:0822 VIA Labs, Inc. USB3.1 Hub             
```

```log
$ sudo journalctl -k
Jan 24 11:38:15 laptop kernel: usb 3-2: new high-speed USB device number 23 using xhci_hcd
Jan 24 11:38:15 laptop kernel: usb 2-2: new SuperSpeed Plus Gen 2x1 USB device number 10 using xhci_hcd
Jan 24 11:38:15 laptop kernel: usb 2-2: New USB device found, idVendor=2109, idProduct=0822, bcdDevice= 6.33
Jan 24 11:38:15 laptop kernel: usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 24 11:38:15 laptop kernel: usb 2-2: Product: USB3.1 Hub             
Jan 24 11:38:15 laptop kernel: usb 2-2: Manufacturer: VIA Labs, Inc.         
Jan 24 11:38:15 laptop kernel: usb 2-2: SerialNumber: 000000001
Jan 24 11:38:15 laptop kernel: hub 2-2:1.0: USB hub found
Jan 24 11:38:15 laptop kernel: hub 2-2:1.0: 4 ports detected
Jan 24 11:38:15 laptop kernel: usb 3-2: New USB device found, idVendor=2109, idProduct=2822, bcdDevice= 6.33
Jan 24 11:38:15 laptop kernel: usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 24 11:38:15 laptop kernel: usb 3-2: Product: USB2.0 Hub             
Jan 24 11:38:15 laptop kernel: usb 3-2: Manufacturer: VIA Labs, Inc.         
Jan 24 11:38:15 laptop kernel: usb 3-2: SerialNumber: 000000001
Jan 24 11:38:15 laptop kernel: hub 3-2:1.0: USB hub found
Jan 24 11:38:15 laptop kernel: hub 3-2:1.0: 5 ports detected
Jan 24 11:38:17 laptop kernel: usb 3-2.3: new full-speed USB device number 24 using xhci_hcd
Jan 24 11:38:17 laptop kernel: usb 3-2.3: New USB device found, idVendor=413c, idProduct=81e3, bcdDevice= 0.69
Jan 24 11:38:17 laptop kernel: usb 3-2.3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Jan 24 11:38:17 laptop kernel: usb 3-2.3: Product: Dell MH3021P
Jan 24 11:38:17 laptop kernel: usb 3-2.3: Manufacturer: Luxshar
Jan 24 11:38:17 laptop kernel: usb 3-2.3: SerialNumber: 20210121.69.0.0
Jan 24 11:38:17 laptop kernel: input: Luxshar Dell MH3021P as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.3/3-2.3:1.3/0003:413C:81E3.000F/input/input50
Jan 24 11:38:17 laptop kernel: input: Luxshar Dell MH3021P Consumer Control as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.3/3-2.3:1.3/0003:413C:81E3.000F/input/input51
Jan 24 11:38:17 laptop kernel: input: Luxshar Dell MH3021P as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.3/3-2.3:1.3/0003:413C:81E3.000F/input/input53
Jan 24 11:38:17 laptop kernel: hid-generic 0003:413C:81E3.000F: input,hiddev3,hidraw7: USB HID v1.11 Device [Luxshar Dell MH3021P] on usb-0000:00:14.0-2.3/input3
Jan 24 11:38:20 laptop kernel: hub 2-2:1.0: set hub depth failed
Jan 24 11:38:20 laptop kernel: usb 3-2.5: new high-speed USB device number 25 using xhci_hcd
Jan 24 11:38:20 laptop kernel: usb 3-2.5: New USB device found, idVendor=2109, idProduct=8884, bcdDevice= 0.01
Jan 24 11:38:20 laptop kernel: usb 3-2.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 24 11:38:20 laptop kernel: usb 3-2.5: Product: Dell MH3021P           
Jan 24 11:38:20 laptop kernel: usb 3-2.5: Manufacturer: VIA Labs, Inc.         
Jan 24 11:38:20 laptop kernel: usb 3-2.5: SerialNumber: 0000000000000001
Jan 24 11:38:20 laptop kernel: usb 2-2: USB disconnect, device number 10
Jan 24 11:38:20 laptop kernel: usb 2-2: new SuperSpeed Plus Gen 2x1 USB device number 11 using xhci_hcd
Jan 24 11:38:20 laptop kernel: usb 2-2: New USB device found, idVendor=2109, idProduct=0822, bcdDevice= 6.33
Jan 24 11:38:20 laptop kernel: usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 24 11:38:20 laptop kernel: usb 2-2: Product: USB3.1 Hub             
Jan 24 11:38:20 laptop kernel: usb 2-2: Manufacturer: VIA Labs, Inc.         
Jan 24 11:38:20 laptop kernel: usb 2-2: SerialNumber: 000000001
Jan 24 11:38:20 laptop kernel: hub 2-2:1.0: USB hub found
Jan 24 11:38:20 laptop kernel: hub 2-2:1.0: 4 ports detected
```

```log
$ usb-devices

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 11 Spd=10000 MxCh= 4
D:  Ver= 3.20 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=2109 ProdID=0822 Rev=06.33
S:  Manufacturer=VIA Labs, Inc.         
S:  Product=USB3.1 Hub             
S:  SerialNumber=000000001
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=13(Int.) MxPS=   2 Ivl=16ms
```

```log
$ sudo lsusb -v

Bus 003 Device 028: ID 2109:8884 VIA Labs, Inc. Dell MH3021P           
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.01
  bDeviceClass          254 Application Specific Interface
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2109 VIA Labs, Inc.
  idProduct          0x8884 
  bcdDevice            0.01
  iManufacturer           1 VIA Labs, Inc.         
  iProduct                2 Dell MH3021P           
  iSerial                 3 0000000000000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0012
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          3 0000000000000001
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        17 
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              3 0000000000000001
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x0051
  bNumDeviceCaps          3
  Billboard Capability:
    bLength                    48
    bDescriptorType            16
    bDevCapabilityType         13
    iAdditionalInfoURL          3 0000000000000001
    bNumberOfAlternateModes     1
    bPreferredAlternateMode     0
    VCONN Power                 0 1W
    bmConfigured                03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
    bcdVersion               1.21
    bAdditionalFailureInfo      0
    bReserved                   0
    Alternate Modes supported by Device Container:
    Alternate Mode 0 : Alternate Mode configuration successful
      wSVID[0]                    0xFF01
      bAlternateMode[0]           0
      iAlternateModeString[0]     3 0000000000000001
  Billboard Alternate Mode Capability:
    bLength                     8
    bDescriptorType            16
    bDevCapabilityType         15
    bIndex                      0
    dwAlternateModeVdo          0x05000000
  Container ID Device Capability:
    bLength                20
    bDescriptorType        16
    bDevCapabilityType      4
    bReserved               0
    ContainerID             {30eef35c-07d5-2549-b001-802d79434c30}
Device Status:     0x0001
  Self Powered

Bus 003 Device 027: ID 413c:81e3 Dell Computer Corp. Dell MH3021P
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x81e3 
  bcdDevice            0.69
  iManufacturer           3 Luxshar
  iProduct                1 Dell MH3021P
  iSerial                 2 20210121.69.0.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x00f9
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength       0x005d
        bInCollection           2
        baInterfaceNr(0)        1
        baInterfaceNr(1)        2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0405 Echo-canceling speakerphone
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            2
        bmaControls(0)     0x0001
          Mute Control
        bmaControls(1)     0x0002
          Volume Control
        bmaControls(2)     0x0002
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               4
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                15
        bDescriptorType        36
        bDescriptorSubtype      8 (EXTENSION_UNIT)
        bUnitID                 4
        wExtensionCode     0x0bda
        bNrInPins               1
        baSourceID(0)           3
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        bControlSize            1
        bmControls(0)        0x01
        iExtension              0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID            14
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            15
        wTerminalType      0x0405 Echo-canceling speakerphone
        bAssocTerminal         14
        bSourceID              16
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                16
        bSourceID              14
        bControlSize            2
        bmaControls(0)     0x0001
          Mute Control
        bmaControls(1)     0x0002
          Volume Control
        bmaControls(2)     0x0002
          Volume Control
        iFeature                0 
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               8
        bRefresh                0
        bSynchAddress           0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag         0x0001 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioStreaming Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay         0x0000
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink          14
        bDelay                  1 frames
        wFormatTag         0x0001 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioStreaming Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay         0x0000
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     504
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               8
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

Bus 003 Device 026: ID 2109:2822 VIA Labs, Inc. USB2.0 Hub             
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x2109 VIA Labs, Inc.
  idProduct          0x2822 
  bcdDevice            6.33
  iManufacturer           1 VIA Labs, Inc.         
  iProduct                2 USB2.0 Hub             
  iSerial                 3 000000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0029
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 
      bInterfaceProtocol      1 Single TT
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 
      bInterfaceProtocol      2 TT per port
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             5
  wHubCharacteristic 0x00e9
    Per-port power switching
    Per-port overcurrent protection
    TT think time 32 FS bits
    Port indicators
  bPwrOn2PwrGood      175 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x20
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0103 power enable connect
   Port 4: 0000.0100 power
   Port 5: 0000.0503 highspeed power enable connect
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x0049
  bNumDeviceCaps          5
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000006
      BESL Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           4 micro seconds
    bU2DevExitLat         231 micro seconds
  Container ID Device Capability:
    bLength                20
    bDescriptorType        16
    bDevCapabilityType      4
    bReserved               0
    ContainerID             {30eef35c-07d5-2549-b001-802d79434c30}
  SuperSpeedPlus USB Device Capability:
    bLength                28
    bDescriptorType        16
    bDevCapabilityType     10
    bmAttributes         0x00000023
      Sublink Speed Attribute count 3
      Sublink Speed ID count 1
    wFunctionalitySupport   0x1100
    bmSublinkSpeedAttr[0]   0x00050030
      Speed Attribute ID: 0 5Gb/s Symmetric RX SuperSpeed
    bmSublinkSpeedAttr[1]   0x000500b0
      Speed Attribute ID: 0 5Gb/s Symmetric TX SuperSpeed
    bmSublinkSpeedAttr[2]   0x000a4031
      Speed Attribute ID: 1 10Gb/s Symmetric RX SuperSpeedPlus
    bmSublinkSpeedAttr[3]   0x000a40b1
      Speed Attribute ID: 1 10Gb/s Symmetric TX SuperSpeedPlus
  ** UNRECOGNIZED:  03 10 0b
Device Status:     0x0001
  Self Powered

Bus 002 Device 013: ID 2109:0822 VIA Labs, Inc. USB3.1 Hub             
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.20
  bDeviceClass            9 Hub
  bDeviceSubClass         0 
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x2109 VIA Labs, Inc.
  idProduct          0x0822 
  bcdDevice            6.33
  iManufacturer           1 VIA Labs, Inc.         
  iProduct                2 USB3.1 Hub             
  iSerial                 3 000000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x001f
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes           19
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               8
        bMaxBurst               0
Hub Descriptor:
  bLength              12
  bDescriptorType      42
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood      175 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  bHubDecLat          0.4 micro seconds
  wHubDelay          2292 nano seconds
  DeviceRemovable    0x00
 Hub Port Status:
   Port 1: 0000.02a0 lowspeed L1
   Port 2: 0000.02a0 lowspeed L1
   Port 3: 0000.02a0 lowspeed L1
   Port 4: 0000.02a0 lowspeed L1
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x0049
  bNumDeviceCaps          5
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000006
      BESL Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           4 micro seconds
    bU2DevExitLat         231 micro seconds
  Container ID Device Capability:
    bLength                20
    bDescriptorType        16
    bDevCapabilityType      4
    bReserved               0
    ContainerID             {30eef35c-07d5-2549-b001-802d79434c30}
  SuperSpeedPlus USB Device Capability:
    bLength                28
    bDescriptorType        16
    bDevCapabilityType     10
    bmAttributes         0x00000023
      Sublink Speed Attribute count 3
      Sublink Speed ID count 1
    wFunctionalitySupport   0x1100
    bmSublinkSpeedAttr[0]   0x00050030
      Speed Attribute ID: 0 5Gb/s Symmetric RX SuperSpeed
    bmSublinkSpeedAttr[1]   0x000500b0
      Speed Attribute ID: 0 5Gb/s Symmetric TX SuperSpeed
    bmSublinkSpeedAttr[2]   0x000a4031
      Speed Attribute ID: 1 10Gb/s Symmetric RX SuperSpeedPlus
    bmSublinkSpeedAttr[3]   0x000a40b1
      Speed Attribute ID: 1 10Gb/s Symmetric TX SuperSpeedPlus
  ** UNRECOGNIZED:  03 10 0b
Device Status:     0x000d
  Self Powered
  U1 Enabled
  U2 Enabled
```
