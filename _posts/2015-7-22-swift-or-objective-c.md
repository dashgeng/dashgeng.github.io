---
layout: post
title: Swift 是否会取代 Objective-C
tags: 
- 人在江湖
---

最近经常在各大网站和论坛上看到关于 Swift 是否会取代 Objective-C 的文章和热烈讨论。我也分析和思考了其中的种种可能。于是就想把自己的观点拿出来与大家分享，希望在不久的将来能够得到一一印证。

### Swift 是否会取代 Objective-C
这一观点我认为是无容置疑的，Objective-C "年迈"是不争的事实。至少它经过一番改造之后仍然缺少很多现代语言的特性，弱于多数如 Java, C# 等"现代"语言。对于大多开发者而言，其使用难度如同 C++ 一般难于驾驭，使得开发和维护成本不断增加。
Swift 的初衷就是希望在开发和维护上弥补 Objective-C 的先天不足，并兼顾"现代"语言特性，能够以简单，易读和更为自然的语法写出优雅的代码。其宗旨就在于更加好用，易用。

### Swift 何时会取代 Objective-C
按照 Apple 的观点，在2016年之后才会大量使用 Swift 来更新现有程序，开发新程序。毕竟一个2014年才推出的新语言，还有很多的不足和缺陷。这些需要时间来弥补。当然，我们能够看到 Swift 的发展是十分迅速的。从2014年6月2日发布 Swift 1.0 开始，到发布 Swift 2.0，只有短短一年的时间。中间经历的多个主要版本的改进，可见 Apple 是对其寄予厚望！
以下是 Swift语言发布的主要版本和发布时间。

- Swift 1.0 发布时间2014年6月2日
- Swift 1.1 发布时间2014年10月20日
- Swift 1.2 发布时间2015年2月9日
- Swift 2.0 发布时间2015年6月8日

在语法层面上，Swift 已经趋近于完善，未来应该不会有大的改动。主要修改预计是增加新的语法，而不会轻易修改现有语法了。

### Cocoa 框架的未来
在 NSHipster 上，Apple 开发领域的大牛 Mattt Thompson 和 Nate Cook 都对 Cocoa 的未来做出了自己的展望。可参考他们的相关文章：[The Death of Cocoa](http://nshipster.com/the-death-of-cocoa/)、[Long Live Cocoa](http://nshipster.com/long-live-cocoa/)

从现实角度出发，完全替换 Cocoa 需要极大的工作量，带来的风险是不可估的。iOS 和 OS X 的开发，紧密的依赖于 Cocoa 框架(以及 Cocoa Touch)，因此在未来的两三年之内，预计 Cocoa 只会在现有基础上支持 Swift 的开发。而且，即使 Apple 决心开发新的框架，估计也会是在 Swift 基本成熟之后(即2016年)的事了。而且，必然会大量保留 Cocoa 的特色，降低开发者的迁移难度。

### 新进开发者对语言的选择
Apple 的成功极大的鼓舞了开发者们纷纷投入其阵营。那么，新进的开发者在语言上是应该学习 Swift 还是学习 Objective-C 呢？ 
我想抱有此观点的开发者不在少数，但我依然认为 Objective-C 是必须要掌握的语言。如上所述，Swift 必须面对历史问题，很大程度上要支持现有的 Objective-C 和 Cocoa 框架。因此，学习 Objective-C 以及阅读其相关文章等资源能使开发者更加深入的理解 iOS 和 OS X 的编程本质。对于掌握 Swift 绝对是一大助力，能使开发者少走很多的弯路。

希望这些观点能够帮助仍在迷茫中的你，同时印证我自己的想法。

*扬帆起航！*

**祝：一帆风顺！**

-- End --