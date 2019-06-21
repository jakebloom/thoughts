---
layout: post
title: The World's Dumbest Smart Home
description: Compromises to avoid having a microphone in my bedroom
date: 20/06/2019
---

About eighteen months ago, I bought an amazon echo. I was looking for an alarm clock that could also tell me the weather, and the echo was on sale at the time.

So I got my echo and it worked well. It was an effective alarm clock, it told me the weather, it could tell me the time back in Sydney and it could stream triple j. [I even wrote an app for it that would read out headlines from the ABC.](https://www.amazon.com/Jake-Bloom-News-Australia-unofficial/dp/B077SXG7JJ) (It gets used by about 500 people per month).

But I could never shake the sense of unease that came with a microphone being in my bedroom. Every day that I got up and got ready for work, every phone call I made to my family, every conversation I had with Zoe was being recorded. 

Eventually the novelty wore off, but the feeling of unease remained. When I moved apartments, I got rid of the echo.

But this presented me with a new problem. In apartments in America, it is very common to not have any lights in the ceiling. The light switch will connect to one plug that you can connect a lamp to. 

I wanted more light in my room without running extension cables all over the floor, and I didn’t want to be sending data about when I wake up and go to sleep to amazon (or google for that matter).

So I decided to build the world’s dumbest smart home. I had the following requirements:
- It had to be totally self reliant, without any cloud service providers and no requests outside the local network
- I wanted to control my desk lights via my phone
- I wanted to keep my regular lamp controlled by the light switch

To implement this, I bought a relay switch power point off amazon, and connected it up to a raspberry pi I had lying around.

I first looked in to [Home Assistant](https://home-assistant.io), an open source project that powers smart homes, but that seemed too heavyweight for me - I only wanted to run one light.

I then looked into [HAP-Python](https://github.com/ikalchev/HAP-python), which implements apple's "HomeKit" protocol, because I thought it would be cool to control my lights from the “Home” app that came with my iPhone. But I wasn’t able to get that working.

So I went right back to basics, and decided to run a web server on the raspberry pi that would control the relay switch. It also serves a web page that contains a light switch made that I built in CSS.

So there you have it. A smart home free from the watch of corporate surveillance. Was it easy? No. Was it worth the extra effort? Maybe. Did I have fun? Yes.

[You can see the source code here.](https://github.com/jakebloom/lightsite)

<style>
  .switch {
    position: absolute;
    background-color: #E6E1C5;
    width: 150px;
    height: 300px;
    border-radius: 10px;
  }

  .switch::before {
    top: 10px;
    border-radius: 10px 10px 0 0;
    content: '';
    width: 150px;
    height: 150px;
    background: #d2cdb4;
    position: absolute;
  }

  .switchcontainer {
    display: flex;
    justify-content: center;
  }
</style>
<div class="switchcontainer">
  <div class="switch" />
</div>