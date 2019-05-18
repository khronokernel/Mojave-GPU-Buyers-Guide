# Mojave-GPU-Buyers-Guide

**Disclaimer: I mention Turing, Pascal and Maxwell to help educate users on what versions of MacOs they're supported on but if you accidentally fell on this page thinking your RTX 2080ti is supported, please read carefully**


So on this sub there’s been quite a few questions regarding which GPU to buy for Mojave ever since the Web Drivers “disappeared”. Though I want to go in depth why the Web Drivers were removed, I’ll give you guys a TL;DR on the situation and a little guide of which GPUs to buy, which to avoid and the pros/cons of each model.

# TL;DR on WebDrivers

&#x200B;

So what’s going on with the Web Drivers? Well the issue seems to go back to the philosophy of both companies, the philosophy of wanting to control the entire software stack for their products. Nvidia want to control every single aspect of their products which is the biggest reason for not having open sourced drivers, and then you look at the company that makes MacOs, iOS and clearly see how they want to control every aspect of their little garden. Think it’s a coincidence both AMD and Intel have open sourced graphics drivers? It seems that Apple has had issues with Web driver quality before and it seems that Mojave was them finally taking a stand and saying either build better drivers or give us control similar to the Kepler series.

So this whole situation means we’re out of luck for any sort of web drivers as these 2 titans clash with neither bending the knee.

# So what GPU should I buy?


So there’s still 2 routes for discrete GPUs you can go, either AMD or Nvidia(Yes, there’s actually natively supported Nvidia cards in Mojave). So I’ll be going over what GPUs are compatible and what features/drawbacks they hold.

Things to remember:

* Mac OS does not support either SLI, Crossfire or GPUs will multiple main cores(like the Radeon Pro Duo)
* Getting audio through HDMI/DisplayPort may require extra work with both AppleALC.kext and some other IO-REG edits

# AMD GPUs


**Vega series Highest Supported OS: Current/Mojave 10.14.4**

So all Vega cards are natively supported with the exclusion of the new Radeon VII but there is some support in the newest MacOs 10.14.5 beta allowing it to operate properly. Another thing to note is that reference design GPUs actually don’t have a fan profile set in MacOs meaning the systems will spin at high RPMs continuously but with an unlocked power play table, we can Overclock/Undervolt these cards and set custom fan profiles just for MacOs.

EDIT: regarding fan RPM, there is no need for addition kexts from VGTab as MacOs 10.14.5 now automatically does this for us

The only brand of GPUs to **avoid with Vegas are XFX and Sapphire**. Reason being is VBIOS communication issues which can't be easily solved with a reference BIOS due to how Vega's powerplay table interacts between the OS and GPU.

Recommended software setting the RPM and power play tables would be [VGTab](https://www.tonymacx86.com/threads/tool-vgtab-control-your-vega-in-macos-without-flashing-the-vbios.268965/). To get power draw monitoring, don't forget to set PP\_DisablePowerContainment to 0.

Supported Cards:

* Vega 56
* Vega 64
* Vega 64 Liquid
* Rx Vega VII (If running MacOs 10.14.5 Beta 1)
* Vega Frontier Edition
* Radeon Pro WX 9100
* Radeon Pro WX 7100


Needed kexts:

* [lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [VGTab fan kext(or something similar)](https://www.tonymacx86.com/threads/tool-vgtab-control-your-vega-in-macos-without-flashing-the-vbios.268965/)


**Radeon 400 series (Polaris) Highest Supported OS: Current/Mojave 10.14.4**

Regarding Polaris, basically every model of card is supported as kong as it’s running a Polaris core(lower end cards like the RX550 run a Lexa core meaning no support in MacOs).

The only brand of GPU **you should** **avoid with the Polaris series would be XFX** as many users have had issues with these cards with viewing Clover and MacOs booting but other users have found fixes/work arounds. This is caused by having an odd VBIOS that doesn't communicate well with MacOs, only real solution is flashing another VBIOS which is not ideal.

Supported cards:

* RX 460/560
* RX 470/570
* RX 480/580
* RX 590
* WX 2100
* WX 3100
* WX 4100
* WX 5100


Needed kexts:

* [lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)


**GCN 3 and older based Cards**

Regarding GCN 3 and older, cards from these generations theoretically will have support for Metal in Mojave but due to how fragmented some of the product stack became meant that some cards may not have support. Generally, HD 7XXX series of GPUs and up are metal compatible but I’ll only list GPUs that have been proven to work.

**Radeon R9 3xx (Fiji) Current/Mojave 10.14.4**

Fiji is also natively supported in Mojave without much issue but we cannot guarantee the success of R5 and R7 cards due to not having many reports of success soon them. Also be wary that differing from the reference design of these cards have many more issues that require a lot of work to get them to run properly

Edit 1:

>There is an error in the list. The R9 290/390 are not supported natively. The 290X/390X are.  
>  
>You need to use a FakeID to get the non-x variants running.

As u/bankopf mentioned, non X variants of the 290/390 cards are none native and need to use a FakeID

Supported cards:

* R7 240
* R7 250
* R9 260/360
* R7 260x/360x
* R7 265
* R7 270/370
* R9 270X / 370X
* R9 280/380
* R9 280x/380x
* R9 390((FakeID needed)
* R9 Nano
* R9 Fury
* R9 Fury x

&#x200B;

&#x200B;

Needed kexts

* [lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

&#x200B;

# Native nVidia GPUs

&#x200B;

**Kepler GPUs (GTX 6xx, 7xx) Highest Supported OS: Current/Mojave 10.14.4**

Currently the only 100% native Nvidia architecture that works with Mojave. Users have reported issues with the GTX 650ti, 660, 660ti but this is caused by a driver issue on Apple’s end by not supporting the GK106 core(or quite poorly as the issue seems to be memory leakage which also affects real Macs). Another issue with this generation is lower end products marketed as first generation Kepler are actually using a Fermi core but have identical counterparts running Kepler cores as well(GF 116 vs GK 107 found in the GT 640). **AND PLEASE NOTICE THAT  GTX 745, 750 and ti VARIANTS ARE NOT INCLUDED, THEY'RE NOT KEPLER**

Supported cards:

Kepler Gen 2:

* GTX Titan (GK 110 Maxwell core)
* GTX Titan Black(GK 110 Maxwell core)
* GTX Titan Z (One of the few dual GPU cards supported in MacOs)
* GTX 780/ti
* GTX 770
* GTX 760/ti
* GT 740
* GT 730
* GT 720
* GT 710

&#x200B;

Kepler Gen 1:

* GTX Titan (GK 110 Maxwell core)
* GTX Titan Black(GK 110 Maxwell core)
* GTX Titan Z (One of the few dual GPU cards supported in MacOs, unfortunately was never truly utilized)
* GTX 690(Another dual GPU card compatible with MacOS)
* GTX 680
* GTX 670
* GTX 660/TI(MUST BE RUNNING A GK 104 core, NOT GK 106)
* GTX 650(MUST BE RUNNING A GK 107 core, NOT GK 106)
* GTX 645(GT 645 is Fermi)
* GT 640(Kepler edition, GK 107/208 core)
* GT 630(Kepler edition, GK 208 core)

&#x200B;

Quadro:

* Quadro 410
* Quadro K420
* Quadro K600
* Quadro K2000/D
* Quadro K4000/D
* Quadro K4200
* Quadro K5000
* Quadro K5200
* Quadro K6000

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

&#x200B;

**Fermi GPUs (GTX 4xx, 5xx) Highest Supported OS: Sierra/High Sierra 10.13.6(with some work, current/Mojave 10.14.4)**

Well Mojave actually pulled official support for these cards from Mojave but thankfully you can just chuck the old High Sierra drivers back in and you’ll be good. Nothing too important to add for Fermi specifically, just understand since it’s no longer OOB you may have odd driver issues so only use your Fermi card in desperation. Users have reported issues with High Sierra so using those drivers can cause some issues. And I won’t make a list of compatible graphics cards due to the nature of no longer being official as I don’t want someone to stumble upon this thinking their GT610 is compatible without any work.

Needed Kexts:

* [GeForce-GF100-Series.kext](https://www.dropbox.com/s/32h43kn0jqvcpoh/GeForce-GF100-Series.kext.zip?dl=0)(You'll also need to replace CoreDisplay from 10.13.4 to 10.14 through ⁨System⁩/Library⁩/⁨Frameworks⁩/CoreDisplay.framework⁩/Versions⁩/A⁩)
* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

&#x200B;

**All Other Nvidia GPUs**

With cards even older than Fermi like Tesla and such, please refer to [Fix Old NVIDIA macOS Mojave](https://github.com/chris1111/Fix-Old-NVIDIA-macOS-Mojave)

# Unsupported nVidia GPUs

&#x200B;

**Turing GPUs (GTX 20xx, 16xx) Highest Supported OS:NONE**

Unfortunately no support in any version of MacOs as no drivers were ever written even for High Sierra. Not much else to add.

These cards include:

* Titan RTX
* RTX 2080/ti
* RTX 2070
* RTX 2060
* GTX 1660/ti
* GTX 1650/ti
* Quadro RTX 4000
* Quadro RTX 5000
* Quadro RTX 6000
* Quadro RTX 8000

&#x200B;

**Pascal GPUs (GTX 10xx) Highest Supported OS: High Sierra 10.13.6**

Well pretty sure most users know what going on with Pascal and Maxwell but I’ll just mention it quick here. No support for these cards in Mojave but MacOs High Sierra 10.13.6 do support these cards with the combination of Nvidia’s somewhat shotty drivers and Lilu+WhateverGreen. Support for Mojave is unlikely

Supported cards:

* GTX Titan X(GP 102-400 Pascal core)
* GTX Titan Xp(GP 102-450 Pascal core)
* GTX 1080/ti
* GTX 1070/ti
* GTX 1060
* GTX 1050/ti
* GT 1030

&#x200B;

Quadro:

* Quadro P400
* Quadro P600
* Quadro P620
* Quadro P1000
* Quadro P2000
* Quadro P4000
* Quadro P5000
* Quadro P6000
* Quadro GP100

&#x200B;

Needed kexts:

* [Nvidia’s Web drivers](https://www.nvidia.com/download/driverResults.aspx/125379/en-us)
* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

&#x200B;

**Maxwell GPUs (GTX 9xx, 745, 750 and ti variant) Highest Supported OS: High Sierra 10.13.6**

Same idea as Pascal, though the naming scheme is a bit odd as the GTX 745, 750 and 750ti are all Maxwell based even though they’re being marketed with the Kepler line so be wary when buying

Supported cards:

* GTX Titan X(GM 200 Maxwell core)
* GTX 980/ti
* GTX 970
* GTX 960
* GTX 950
* GTX 750/ti
* GTX 745

&#x200B;

Quadro:

* Quadro K620
* Quadro K1200
* Quadro K220
* Quadro M2000
* Quadro M4000
* Quadro M5000
* Quadro M6000
* NVS 510

&#x200B;

Needed kexts:

* [Nvidia’s Web drivers](https://www.nvidia.com/download/driverResults.aspx/125379/en-us)
* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

# Intel's Integrated Graphics

So I'll be going over the compatible iGPUs present in intel's CPUs, main thing to note is that you'll need to apply the FrameBuffer patch to your system to get things to work properly. [Please refer to this post for more info on Framebuffer patching as it goes in depth on how to get your system running](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271). We will also be excluding iGPUs present in Pentiums, Celerons and Atom CPUs as they've never been supported natively and require quite a bit of extra work to get them working

&#x200B;

**Westmere i3/5/7-xxx Highest Supported OS: High Sierra 10.13.6**

Unfortunately Mojave dropped support for these iGPUs but luckily using a similar method to Fermi we can actually get these iGPUs working by using old kexts(though no Metal support so things are a bit iffy). I won't link any of the files myself so do be wary when downloading kexts off the internet

* HD Graphics (yup, that's all they called them)

&#x200B;

Files needed:

* GPUSupport.framework
* OpenGL.framework

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Sandy Bridge i3/5/7-2XXX Highest Supported OS: High Sierra 10.13.6(With a bit of work, current/Mojave 10.14.4)**

Unfortunately Mojave dropped support for these iGPUs but luckily using a similar method to Fermi we can actually get these iGPUs working by using old kexts(though no Metal support so things are a bit iffy). I won't link any of the files myself so do be wary when downloading kexts off the internet

&#x200B;

Supported iGPUs:

* HD 2000
* HD 3000

&#x200B;

Files needed for HD 2000:

* AppleIntelHDGraphicsFB.kext
* AppleIntelHDGraphicsGA.plugin
* AppleIntelHDGraphicsGLDriver.bundle
* AppleIntelHDGraphicsVADriver.bundle

&#x200B;

Files needed for HD 2000:

* AppleIntelHD3000Graphics.kext
* AppleIntelHD3000GraphicsGA.plugin
* AppleIntelHD3000GraphicsGLDriver.bundle
* AppleIntelHD3000GraphicsVADriver.bundle
* AppleIntelSNBGraphicsFB.kext
* AppleIntelSNBVA.bundle

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Ivy Bridge i3/5/7-3XXX Highest Supported OS: Current/Mojave 10.14.4**

Regarding the HD 4000, it's completely native with Mojave. The HD 2500 on the other hand only has partial support in Mojave for quick sync features as hardware acceleration is [unsupported](https://olarila.com/forum/viewtopic.php?t=7714)

&#x200B;

Supported iGPUs:

* HD 2500
* HD 4000

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Haswell i3/5/7-4XXX Highest Supported OS: Current/Mojave 10.14.4**

All iGPUs are supported here, no issues to report

Supported iGPUs:

* HD 4200
* HD 4400
* HD 4600
* HD 5000
* HD 5100
* HD P4600(Theoretically)
* HD P4700(Theoretically)

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Broadwell i3/5/7-5XXX Highest Supported OS: Current/Mojave 10.14.4**

All iGPUs are supported here, no issues to report

Supported iGPUs:

* HD 5300
* HD 5500
* HD 5600
* HD 6000
* HD 6100
* HD 6200
* HD P5700(Theoretically)
* Iris Pro P6300

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Skylake i3/5/7-6XXX Highest Supported OS: Current/Mojave 10.14.4**

All iGPUs are supported here, no issues to report

Supported iGPUs:

* HD 510
* HD 515
* HD 520
* HD 530
* HD P530
* Iris 540
* Iris 550
* Iris Pro 580
* Iris Pro P555
* Iris Pro P580

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Kabylake i3/5/7-7XXX Highest Supported OS: Current/Mojave 10.14.4**

Most iGPUs are supported here excluding the HD 610 present in the Pentium G4560

Supported iGPUs:

* HD 615
* HD 620
* HD 630
* Iris Plus 640
* Iris Plus 650

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

**Kabylake refresh/ Coffeelake i3/5/7-8XXX/9XXX Highest Supported OS: Current/Mojave 10.14.4**

All iGPUs are supported here, though pay attention as the i3 8100 and 8350k use a different UHD 630 than the rest of the CPU family

* UHD 610
* UHD 620
* UHD 630
* Iris Plus 655

&#x200B;

Needed kexts:

* [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
* [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)
* [IntelFrameBuffer Patching guide](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/?tab=comments#comment-2626271)

&#x200B;

# AMD's Integrated Graphics

Well I was originally just gonna say incompatible but they're not. Much more research will need to be done but will add to this later

# Hey I'm lazy, just tell me what to buy

So you just want a GPU recommendation? Well honestly in the current situation the only cards we'd recommend would be from AMD that are either Polaris(Rx 4xx, 5xx) or newer as GCN 3 and older can loose support at any time and the same applies for Kepler. Here's the cards we recommend and do remember that reference cards are generally the safest solution\*\*(AVOID XFX AT ALL COSTS)\*\*:

* Rx 460/560
* Rx 470/570
* Rx 480/580
* Rx 590
* Rx Vega 56
* Rx Vega 64
* Rx Vega VII (If running MacOs 10.14.5 Beta 1)

&#x200B;

Hopefully this little guide helps you, if you have anything else you'd like to add feel free to mention and I'll look into it. I'm fairly certain I forgot something along the way

&#x200B;

Last updated for MacOs 10.14.5 Beta 4

&#x200B;

\- Your local neighbourhood Hackintosh Slav

&#x200B;

Edit 1: As u/bankopf mentioned, non X variants of the R9 series are none native and need to use a FakeID

Edit 2: Added a bit more info as suggested by u/midi1996, specific things added/changed:

* Highest Supported OS
* Changed order of nVidia GPUs for native cards first
* GCN 3 cards differing from reference have many more issues
* Avoid XFX for both Polaris and Vega series cards due to weird VBIOSes that don't play nicely with MacOs
* REMINDING PEOPLE GTX 745, 750 and TI VARIANT ARE NOT KEPLER
* Adding intel HD graphics
* Adding placeholder for AMD APUs
* Adding broken hyperlinks(yay)

Edit 3: Added more info on Turing

Edit 4: Added **NVS 510** as mentioned by trs96

Edit 5: Added GTX 1650/ti, Titan RTX and renamed 1160/ti to proper names(all credit to u/midi1996)

Edit 6: Vega Powerplay table's update with MacOs 10.14.5

Edit 7: Added more GPUs to GCN 3 cards

Edit 8: Added work around for Fermi Cards
