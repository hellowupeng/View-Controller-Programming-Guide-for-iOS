## Customizing the Transition Animationss

过渡动画提供关于应用界面变化的视觉反馈。UIKit提供了一套标准的过渡样式来在呈现视图控制器时使用，并且你能用自己的自定义过渡来补充标准的过渡。

###### 过渡动画序列

过渡动画用另一个视图控制器的内容交换一个视图控制器的内容。存在两种过渡类型：presentations 和 dismissals。presentation 过渡添加新的视图控制器到应用的视图控制器层次结构，然而 dismissals 过渡从视图控制器层次结构移除一个或多个视图控制器。

实现过渡动画需要许多对象。UIKit提供在过渡里涉及的所有对象的默认版本，你可以自定义所有或部分对象。如果你选择正确的一套对象，你应该能只用少量代码创建你自己的动画。如果你利用 UIKit 提供的现成代码，即使包括交互的动画也能被容易地实现。

**Transitioning 代理**

**自定义动画序列**

**Transitioning Context 对象**

**Transition 协调器（Coordinator）**

###### **使用**自定义动画呈现视图控制器

###### 实现 Transition 代理

###### 实现你的 Animator 对象

###### 添加 Interactivity 到你的 Transitions

###### 创建和 Transition 一起运行的动画

###### 使用 Prsentation 控制器和你的动画