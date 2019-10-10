---
title: How I became a cyborg pt1
layout: post
date: 2019-10-10
type: "post"
featured: "../../2019/echo-aorta-valve-regurgitation.jpg"
---

## Close Encounters of the Third Kind

"We really need to do something about the valve. We've passed the point where we can wait two more years to see how it progresses."

I was silent for a while, so the cardiologist asked "do you understand what I mean?"

"Like, I need a transplant from a pig heart?", I asked.

"Well, given your age an artificial valve is more likely."

It was clear my heart was fucked. I knew it wasn't a good sign when the doctor sounded more and more worried as she looked at my heart, and hurried in colleagues to get a second and third opinion. Words like "bulging" and "hypertrophy" didn't mean much to to me and I couldn't really ask for clarification since they were looking at my heart through a gigantic tube stuck down my throat. After the procedure, the doctor didn't want to discuss the results with me, saying that the cardiologist would explain everything. She just assured me that "everything will work out fine"; implying that things were, in fact, not fine.

The cardiologist revealed the severity of the issue. _Normal_ hearts have a bunch of valves that make sure blood can only flow in one direction. The aorta valve specifically closes off your heart after each heartbeat to make sure the blood flows to your organs instead of back into your heart. My aorta valve, however, missed that memo. It leaked. Like a lot. Probably a birth defect. My heart took this like a boss for most of my life and just compensated the fuck out of it, but it was starting to take its toll; my heart was becoming enlarged.

{{< fancybox path="/img/2019/" file="echo-aorta-valve-intersection.jpg"  caption="Frontal image of the bad valve. This should normally look like a Mercedes logo; showing the three leaflets of the valve. However, only the top-left leaflet of this valve is regular. The two others are fused together and badly damaged." >}}

{{< fancybox path="/img/2019/" file="echo-aorta-valve-regurgitation.jpg"  caption="Side view of the valve when it's closed with my heart on the left and the aorta on the right. The brightly colored stream on the left is blood going the wrong way; it flows back in to my heart, leaking through the closed valve." >}}

Despite this issue, the cardiologist was also optimistic.

"The good news is that, because we found it so early, your heart should be able to recover after we fix the valve. However, really need to do something about it in time. What do you have planned the following weeks?"

I have to admit that 95% of my brain was focused on how his definition of "in time" was wildly different from mine. "umm, I have some time available, I think.."

"Great! You can discuss the details with the secretary."

Before I knew it, the secretary was calling different departments to schedule a bunch of preparatory exams. Open Heart surgery is pretty gruelling to your body so they wanted to make sure I didn't have any other issues. There was a lot that needed to be done and my brain jumped on it like any other project. Emotionally detached, as if it was a complicated process to fix my computer. I scheduled the appointments, read up on the illness and the procedures and informed family and friends.

There was still some uncertainty about the extent of the issue. The issue with my valve was congenital; it just didn't get the memo on how to do this "valve" thing properly and the doctors wanted to see if any other parts of my heart and veins were slacking off. They did this using a coronarography, or "an alien's wet dream", as I like to call it. They opened two veins in my groin, put in long probes to reach my heart, injected a bunch of contrast fluid, and watched it flow using a Rontgen scan. To top it all off, this procedure was done while I was awake and I could follow along on a giant screen next to me. If this sound uncomfortable, that's probably because it is. Thank god I live in Belgium; just imagine living in the US and becoming financially ruined while some doctors reenact the final scene of "the fourth kind" on you..

Thankfully, the result of the coronarography was positive: the other parts of my heart were nicely executing their assigned tasks, and the surgeons were once again paid to probe a fellow human being. Even better, I now had a bunch of cool videos showing how my heart (mal)functioned.

<!-- {{< youtube id="OFHO9u5H48U" autoplay="true" caption="test">}} -->

> <video width="480" height="480" autoplay loop muted>
>   <source src="/img/2019/coronaro-aorta-valve-regurgitation.mp4" type="video/mp4">
> Your browser does not support the video tag.
> </video>
>
> This video shows a probe injecting contrast fluid in my aorta. Most of the fluid is pumped up through the aorta to the rest of the body. However, due to the leaking valve, part of the fluid is sucked down, back into the left ventricle of the heart itself.

<!--
```bash
# Export images in DICOM file to jpg
mogrify -format jpg F000001
# Create mp4 video file from sequence of jpg images
ffmpeg -framerate 15 -i F000001-%000d.jpg -c:v libx264 -profile:v high -crf 20 -pix_fmt yuv420p output.mp4
```

source: https://askubuntu.com/a/610945/172367
-->

Next step: the heart surgery itself! We scheduled it about six weeks after the coronarography so that I had some time to finish up at work and go on a holiday. However, some complications foiled the plan of finishing up at work. All the probing in my groin tore one of my veins, causing a pseudo-aneurism. After a week of trying to fix it from the outside, the doctors gave up and did a surgery under full anesthesia to sew everything back together. Long story short; I ended up losing four of those six weeks to recovering from the coronarography. Thankfully, the doctor cleared me to go on a holiday after that.

<!--

```
# Convert images into jpg; manually specify contrast
mogrify -define dcm:window=525X3050 -format jpg *
# Convert jpgs into video
ffmpeg -framerate 15 -i F%06d.jpg -c:v libx264 -profile:v high -crf 20 -pix_fmt yuv420p -vf scale=720:-2 output.mp4
```
-->
