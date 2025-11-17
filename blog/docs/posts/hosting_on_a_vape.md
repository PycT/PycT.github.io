---
date: 2025-09-16
categories:
    - tech
    - natural-intelligence
---

!!! Quote

    The chip is marked PUYA C642F15, which wasn’t very helpful. I was pretty sure it was a PY32F002A, but after poking around with pyOCD, I noticed that the flash was 24k and we have 3k of RAM. The extra flash meant that it was more likely a PY32F002B, which is actually a very different chip.1


    So here are the specs of a microcontroller so bad, it’s basically disposable:


    24MHz Coretex M0+
    24KiB of Flash Storage
    3KiB of Static RAM
    a few peripherals, none of which we will use.

    You may look at those specs and think that it’s not much to work with. I don’t blame you, a 10y old phone can barely load google, and this is about 100x slower. I on the other hand see a blazingly fast web server.


[bogdanthegeek.github.io/blog/projects/vapeserver/](https://bogdanthegeek.github.io/blog/projects/vapeserver/)