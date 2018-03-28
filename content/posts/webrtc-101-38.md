---
title: "WebRTC 101"
slug: "webrtc-101"
tags: ["WebRTC", "Javascript", "Apprenticeship"]
date: 2018-03-28
---

Tomorrow I will have a 5 minutes presentation about WebRTC, I thought writing a blog post about it would help to freshen my mind.

> So, what is WebRTC?

RTC part in WebRTC stands for `Real Time Communication`, hence WebRTC aims to create networking devices from browsers. There were some initiatives before WebRTC too, we needed Java applets or we needed to download untrustworthy plug-ins to capture video and broadcast it over browser. Apple had its own protocol for this need, we know it as FaceTime, and in 2010 Steve Jobs suggested to make FaceTime an open standard. Afterwards, Apple failed a law suit against [a tech company](https://beta.techcrunch.com/2012/11/07/u-s-court-orders-apple-to-pay-368-million-damages-for-facetime-patent-infringement/?_ga=2.91112090.1688445734.1522240870-1938224401.1522240870), then kept quiet about opening FaceTime.

After WebRTC, every modern browser started to implement specifications and the networking plug-ins became obsolete. Even though there were some differences between Firefox's and Chrome's API's having similar API's made it easier for companies to implement their own solutions. Since companies already had working software with their plug-ins, most of them didn't bother to implement their WebRTC client, but Google found a radical way to enforce it. As of version 42, Google removed support for NPAPI support, which most of the plugins used.

Enough history, so basically, WebRTC provides some functions to access camera and microphone of user, by the permission of the user of course. Provides methods for creating `Session Description Protocol (SDP)` to complete signalization. Anyone could create communicate two parties by the help of this SDP's.

What you need to do is;

##### Caller Side;

* Get user permission with `navigator.getUserMedia` method
* Create a peer connection for caller with `RTCPeerConnection` class - keep returned value -
* Create offer, which yields SDP for the caller party by the help of `connection.createOffer` method
* Set returned SDP as localDescription by the help of the `connection.setLocalDescription` method
* Ship the SDP to callee

##### Callee Side;

* Get user permission with `navigator.getUserMedia` method
* Create a peer connection for caller with `RTCPeerConnection` class - keep returned value -
* Set remote description to the connection with `connection.setRemoteDescription`
* Create answer for caller side's SDP, which generates an answer SDP for caller by the help of `connection.createAnswer` method
* Set the created answer as local description with `connection.setLocalDescription`
* Ship the SDP to caller

##### Caller Side Again

* Set answer sdp as remoteDescription with `connection.setRemoteDescription`

After completing this process, in a short while -depends on the type of the connection-, the media connection will be completed.

There are so much more to discover about WebRTC. There are `STUN`, `TURN` or `peer to peer` connection types. You can also create `dataChannel` to achieve file transfer, screen sharing. You can create conference servers, call center applications with it. It's fantastic to have such a useful library in our browsers.
