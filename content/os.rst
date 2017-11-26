============
操作系统入门
============

:date: 2015-01-15
:slug: how-to-learn-operating-system
:status: draft

好的操作系统教程很少。很多教程都是从bootloader该怎么写开始的，而bootloader一点都不好写。比如我就照着各种教程在bootloader上死了无数次了。

.. more

首先这是在学写操作系统，而不是把每个问题都搞对，先跑起来才是最重要的事。能绕过的就应该绕过，有的抄的代码就应该抄，而不是自己写。从这个角度看，MIT 6.828 Lab里的JOS是个不错的例子。

JOS的问题是，他帮你把必要的非核心代码都实现了，也还是自己去实现了个bootloader，有点过头了，并不适合一个人从零开始学操作系统。用QEMU是没错的，实际上QEMU有-kernel参数，可以直接启动一个elf格式的支持multiboot的内核，并不需要自己写bootloader。启动需要的硬件信息也可以直接从multiboot info里取到，并不需要自己去取。自己去取更麻烦，各种历史遗留问题一点都不好处理。
