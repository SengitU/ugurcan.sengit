---
title: "Software Should Be More Like Hardware"
slug: "software-should-be-more-like-hardware"
tags: ["hardware", "software development", "apprenticeship"]
date: 2018-07-09
---

I've always wanted to build a desktop computer for myself. One that I can understand my needs and buy my sub-components according to it. Fear of not being able to assemble it or even worse, burning my components while trying was holding me back for a long time now. I am quite surprised to see how easy it was.

I've studied electrical and electronics engineering which might make you think _What the hell? You should be able to assemble, what did they teach you?_. But this is exactly the reason I was afraid. To elaborate, in our classes, we learnt how to assemble a circuit to work towards your goals. Let's say you have a simple breadboard* like this;

![ ](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/400_points_breadboard.jpg/1200px-400_points_breadboard.jpg)

You can see + and - signs and provide power to your circuit accordingly. In order to connect an operational amplifier* to this board, you need to read the datasheet of the product to understand which leg of the component represent which output or input. Opamp is the easy one, in order to connect a 555 oscillator you need to understand and connect the following legs accordingly;

![ ](http://hades.mech.northwestern.edu/images/3/34/555_astable_circuit.gif)

This process doesn't scale in my mind. I thought I've needed to learn my graphics card's IO ports in order to connect it to my motherboard, not to mention I needed to know datasheet of my motherboard. Feels overwhelming when you want to assemble every individual component to your motherboard, doesn't it?

The truth is different, I was shocked to see how fail-safe each component is. Sockets of the motherboard and the components designed to fit together. They designed it in a way that a case fan is only compatible with SYS_FAN port. Furthermore, they have some solid barriers to make sure you can't connect it in reverse order.

![ ](http://www.playtool.com/pages/psuconnectors/all20plus4.jpg)

Can you observe the shapes of the pins? Some of them are square shaped, while some of them are hexagons. These little obstacles force you to connect your socket in a certain way, isn't it brilliant? The hardware prevents you from basic but expensive mistakes. Even though I didn't have much experience in the context, I've succeeded to assemble my hardware. I think it's so easy that everyone can assemble it. Because we learnt the best practices for hardware over time, yet the main problem is here to stay, **software**.

After assembling my hardware and installing my operating system, I had a software problem lasted like 3 or 4 days. Apart from my individual software problem(which I will write a blog post about), the trustworthiness provided by the hardware was fascinating. Honestly, I don't think we provide such level of trustworthiness as software developers. For a complete beginner, it will be extremely hard to build an application, yet it was so easy to build a computer from scratch. Even in the advanced levels, our API's are not intuitive enough and requires reading and understanding, while in hardware it's almost impossible to commit mistakes.

All of these make me think of Bret Victor's talk about the [future of programming](https://www.youtube.com/watch?v=8pTEmbeENF4). We failed to create a way to communicate between services, then we created something called API. The problem with APIs is they are strictly dependent on the understanding of humans which use or create them. This is not the best way to solve this problem since humankind can easily be mistaken.

### Citation
- Breadboards: https://en.wikipedia.org/wiki/Breadboard
- Operational Amplifier: https://en.wikipedia.org/wiki/Operational_amplifier
- 555 oscillator: https://en.wikipedia.org/wiki/555_timer_IC
- PSU connectors: http://www.playtool.com/pages/psuconnectors/connectors.html#atxmain20plus4
