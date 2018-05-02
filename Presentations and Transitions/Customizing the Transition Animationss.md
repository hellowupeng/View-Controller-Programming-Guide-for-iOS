## Customizing the Transition Animationss

过渡动画提供关于应用界面变化的视觉反馈。UIKit提供了一套标准的过渡样式来在呈现视图控制器时使用，并且你能用自己的自定义过渡来补充标准的过渡。

###### 过渡动画序列

过渡动画用另一个视图控制器的内容交换一个视图控制器的内容。存在两种过渡类型：presentations 和 dismissals。presentation 过渡添加新的视图控制器到应用的视图控制器层次结构，然而 dismissals 过渡从视图控制器层次结构移除一个或多个视图控制器。

实现过渡动画需要许多对象。UIKit提供在过渡里涉及的所有对象的默认版本，你可以自定义所有或部分对象。如果你选择正确的一套对象，你应该能只用少量代码创建你自己的动画。如果你利用 UIKit 提供的现成代码，即使包括交互的动画也能被容易地实现。

**Transitioning 代理**

transition 代理是 transition 动画和自定义 presentation 的起点。Transition 代理是一个你定义并遵循 UIViewControllerTransitioningDelegate 协议的对象。它的工作是提供 UIKit 以下对象：

- **Animator 对象**。Animator 对象负责创建用于揭露或隐藏视图控制器视图的动画。Transition 代理能为 present 和 dismiss 视图控制器提供独有的 animator 对象。Animator 对象遵循 UIViewControllerAnimatedTransitioning 协议。

- **交互式 animator 对象**。交互式 animator 对象使用触摸事件和手势识别器驱动自定义动画的时间。交互式 animator 对象遵循 UIViewControllerInteractiveTransitioning 协议。

  创建交互式 animator 最容易的方式是创建 UIPercentDrivenInteractiveTransition 类的子类并添加事件处理代码到子类。那个类控制使用存在的 animator 对象创建的动画的时间。如果你创建自己的交互式 animator，你必须自己渲染动画的每帧。

- **Presentation 控制器**。视图控制器在屏幕上期间 presentation 控制器管理 presentation 样式。系统为内建的 presentation 样式提供 presentation 控制器并且你也能为你自己的 presentation 样式提供自定义的 presentation 控制器，查看 Creating Custom Presentations。



**自定义动画序列**

**Transitioning Context 对象**

**Transition 协调器（Coordinator）

###### **使用**自定义动画呈现视图控制器

###### 实现 Transition 代理

###### 实现你的 Animator 对象

###### 添加 Interactivity 到你的 Transitions

###### 创建和 Transition 一起运行的动画

###### 使用 Prsentation 控制器和你的动画