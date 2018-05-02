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

分配 transition 代理给视图控制器的 transitioningDelegate 属性告诉 UIKit 你想要执行自定义的 transition 或 presentation。你的代理能在它提供的对象上做出选择。如果你不提供 animator 对象，UIKit 使用视图控制器的 modalTransitionStyle 属性里的标准 transition 动画。

图10-1展示了 transition 代理和 animator 对象到被展示视图控制器的关系。presentation 控制器只在视图控制器的 modalPresentationStyle 属性被设置为 UIModalPresentationCustom 时使用。

![VCPG_custom-presentation-and-animator-objects_10-1_2x](/Users/andywu/Documents/iOS/View-Controller-Programming-Guide-for-iOS/resources/VCPG_custom-presentation-and-animator-objects_10-1_2x.png)

关于如何实现你的 transitioning 代理的信息，查看 Implementing the Transitioning Delegate。关于 transitioning 代理对象的方法的更多信息，查看 UIViewControllerTransitioningDelegate Protocol Reference。

**自定义动画序列**

当被展示的视图控制器的 transitioningDelegate 属性包含一个有效对象时，UIKit 使用你提供的自定义 animator 对象呈现它。当它准备呈现时，UIKit 调用你的 transitioning 代理的 animationControllerForPresentedController:presentingController:sourceController: 方法来获取自定义 animator 对象。如果对象是可用的，UIKit 执行以下步骤：

1. UIKit 调用 transitioning 代理的 interactionControllerForPresentation: 方法查看交互式 animator 对象是否可用。如果那个方法返回 nil，UIKit 执行不带交互的动画。

**Transitioning Context 对象**

**Transition 协调器（Coordinator）

###### **使用**自定义动画呈现视图控制器

###### 实现 Transition 代理

###### 实现你的 Animator 对象

###### 添加 Interactivity 到你的 Transitions

###### 创建和 Transition 一起运行的动画

###### 使用 Prsentation 控制器和你的动画