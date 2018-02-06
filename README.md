# iOS 开发面试问题

受 [Front end Developer Interview Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions) 启发，制作了这份 iOS 面试问题列表。

面试 iOS 开发时，切入点很重要，不同的切入点会导致不同的结果，没有找到合适的切入点也无法对应聘者有一个全面的了解。所以这份面试问题列表更多的是提供方向，没有固定的答案，而且可以根据应聘者的回应引出更多有意思深层次的讨论。

如果有不错的问题，欢迎 Pull Request :)

## 一般性问题
* 最近这两天你有学到什么知识/技能么？
* 最近有做过比较酷或者比较有挑战的项目么？
* 最近看过的书/文章有哪些？
sunny，onecat，简书iOS技术专栏，伯乐在线，objc.io 等  
Effective Objective-C 2.0：编写高质量iOS与OS X代码的52个有效方法
Objective-C高级编程:iOS与OS X多线程和内存管理

* 如何向一个只接触过互联网的孩子解释「电视」？
* 为什么要学习编程，编程对你而言的乐趣在哪儿？
* 如果一个函数10次中有7次正确，3次错误，问题可能出现在哪里？
* 自身最大优点是什么，怎么证明？
* 有没有在 GitHub 上发布过开源代码，参与过开源项目？
* 你最近遇到过的一个技术挑战是什么？怎么解决的？
* 开发常用的工具有哪些？
sourcetree，charles，helm，json校验，vpn 
* 熟悉 CocoaPods 么？能大概讲一下工作原理么？
* 最常用的版本控制工具是什么，能大概讲讲原理么？
* 今年你最想掌握的一门技术是什么？为什么？目前已经做到了哪个程度？
* 你一般是怎么用 Instruments 的？
* 你一般是如何调试 Bug 的？
* 你在你的项目中用到了哪些设计模式？
* 如何实现单例，单例会有什么弊端？
* iOS 是如何管理内存的？

## 知识性问题
* 什么是响应链，它是怎么工作的？
* 如何访问并修改一个类的私有属性？
* iOS Extension 是什么？能列举几个常用的 Extension 么？

* 如何把一个包含自定义对象的数组序列化到磁盘？
实现NSCopying协议
重写copyWithZone

* Apple Pay 是什么？它的大概工作流程是怎样的？
* iOS 的沙盒目录结构是怎样的？ App Bundle 里面都有什么？
* iOS 的签名机制大概是怎样的？
* iOS 7的多任务添加了哪两个新的 API? 各自的使用场景是什么？
* Objective-C 的 `class` 是如何实现的？`Selector` 是如何被转化为 C 语言的函数调用的？
* `UIScrollView` 大概是如何实现的，它是如何捕捉、响应手势的？

* Objective-C 如何对已有的方法，添加自己的功能代码以实现类似记录日志这样的功能？
runtime  replaceMethod

* `+load` 和 `+initialize` 的区别是什么？

* 如何让 Category 支持属性？
runtime的  objc_getassociatobject

* `NSOperation` 相比于 GCD 有哪些优势？
* `strong` / `weak` / `unsafe_unretained` 的区别？
* 如何为 Class 定义一个对外只读对内可读写的属性?
* Objective-C 中，meta-class 指的是什么？
* `UIView` 和 `CALayer` 之间的关系？
* `+[UIView animateWithDuration:animations:completion:]` 内部大概是如何实现的？
* 什么时候会发生「隐式动画」？
* 如何处理异步的网络请求？
* `frame` 和 `bounds` 的区别是什么？
frame包含了其位置是当前视图相对于父视图的位置，和其大小。而bounds是自身的大小
* 如何把一张大图缩小为1/4大小的缩略图？
* 一个 App 会处于哪些状态？
前台，后台，
* Push Notification 是如何工作的？
* 什么是 Runloop？
* Toll-Free Bridging 是什么？什么情况下会使用？
* 当系统出现内存警告时会发生什么？
* 什么是 `Protocol`，Delegate 一般是怎么用的？
* autorelease 对象在什么情况下会被释放？
线程结束时，runloop结束了则自动释放池清空
当手机内存不够，或收集的autorelease的对象过多时，runloop进入休眠时也会释放，然后runloop唤醒时重建

* UIWebView 有哪些性能问题？有没有可替代的方案。
内存泄漏。 wkwebview 

* 为什么 NotificationCenter 要 removeObserver? 如何实现自动 remove?

* 当 `TableView` 的 `Cell` 改变时，如何让这些改变以动画的形式呈现？
rowAnimation
* 什么是 `Method Swizzle`，什么情况下会使用？


## 经验类问题
* 为什么 `UIScrollView` 的滚动会导致 `NSTimer` 失效？
滚动时，runloop的mode 变为tracking模式
而Timer是默认添加到runloop的defaultmode的

* 为什么当 Core Animation 完成时，layer 又会恢复到原先的状态？
我们看到的动画的layer其实是动画数，而原位置的layer是视图数
需要再动画树运动完成时，手动将原位置的视图数移动动画结束位置

* 你会如何存储用户的一些敏感信息，如登录的 token。
NSKeyChain

* 有用过一些开源组件吧，能简单说几个么，大概说说它们的使用场景实现。
JSONModel， runtime 字典转模型
SDWebImage，加载网络图片有缓存

* 什么时候会发生 `EXC BAD ACCESS` 异常？
这个对象已经被释放了，然后还去访问时
* 什么时候会使用 Core Graphics，有什么注意事项么？
* NSNotification 和 KVO 的使用场景？
NSNotification 一般用于1个改变，影响到多个不太相关的类
* 使用 Block 时需要注意哪些问题？
* `performSelector:withObject:afterDelay:` 内部大概是怎么实现的，有什么注意事项么？

* 如何播放 GIF 图片，有什么优化方案么？

* 使用 `NSUserDefaults` 时，如何处理布尔的默认值？(比如返回 NO，不知道是真的 NO 还是没有设置过)
一般这种情况，我都是先判断是否为YES啊
* 有哪几种方式可以对图片进行缩放，使用 CoreGraphics 缩放时有什么注意事项？

* 哪些途径可以让 ViewController 瘦下来？
拆分出ViewModel，处理业务逻辑

* 有哪些常见的 Crash 场景？ 
字典setValue时为nil
数组越界
访问野指针
访问一个未实现的方法 EXC BAD ACCESS
VC视图栈跳转时，can not add subview


## 综合类问题
* 设计一个可以无限滚动并且支持自动滚动的 SlideShow。
* 设计一个进度条。
* 设计一套大文件（如上百M的视频）下载方案。
* 如果让你来实现 `dispatch_once`，你会怎么做？
* 设计一个类似 iOS 主屏可以下拉出现 Spotlight 的系统。(对 UIScrollView 的理解程度)

## 编程实现
* 简述[「Snakes and Ladders」](http://en.wikipedia.org/wiki/Snakes_and_Ladders)的实现思路(这道题比较容易阐述清楚，且难度适中)

## 参考

* http://way2ios.com/development/ios-development-2/iphone-interview-question-answers/
* https://blackpixel.com/writing/2013/04/interview-questions-for-ios-and-mac-developers-1.html
* https://github.com/CameronBanga/iOS-Developer-and-Designer-Interview-Questions

