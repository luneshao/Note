# CSS 架构
## 1.BEM 命名方式
[原文链接](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
    BEM:
* B: .block represents the higher level of an abstraction or component.
         表示一个抽象或组件。
* E: .block__element represents a descendent of .block that helps form .block as a whole.
         表示组件的子孙组件，以形成一个完整的组件。
* M: .block--modifier represents a different state or version of .block.
         表示一个不同状态或版本的组件。
## 2.命名空间
[原文链接](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
* o: Signify that something is an Object, and that it may be used in any number of unrelated 
         contexts to the one you can currently see it in.Making modifications to these types of class
         could potentially have knock-on effects in a lot of other unrelated places. Tread carefully.
         一个对象，可以在任意位置复用。当修改时，会产生连锁反应，谨慎修改。
* c: Signify that something is a Component. This is a concrete, implementation-specific piece of UI. 
         All of the changes you make to its styles should be detectable in the context you’re currently looking at.
         Modifying these styles should be safe and have no side effects.
         一个组件，这是一个具体的，特定于实现的ui。所有的改变仅发生在当前上下文。修改这些样式是安全的，没有连锁反应。
* u: Signify that this class is a Utility class. It has a very specific role (often providing only one declaration) 
         and should not be bound onto or changed. It can be reused and is not tied to any specific piece of UI. 
         You will probably recognise this namespace from libraries and methodologies like SUIT.
         实用类，通常只提供一个声明，不应该被绑定到或更改。
* t: Signify that a class is responsible for adding a Theme to a view. It lets us know that UI Components’ 
         current cosmetic appearance may be due to the presence of a theme.
         主题，表示当前ui组件的行为可能是因为主题的存在。
* is,has: Signify that the piece of UI in question is currently styled a certain way because of a state or condition. 
         This stateful namespace is gorgeous, and comes from SMACSS. It tells us that the DOM currently has a temporary,
         optional, or short-lived style applied to it due to a certain state being invoked.
         状态命名，表示调用了某种状态。
* js: Signify that this piece of the DOM has some behaviour acting upon it, and that JavaScript binds onto it to provide that behaviour.
         If you’re not a developer working with JavaScript, leave these well alone.
         需要绑定js提供行为。
## 3.css架构
[原文链接](https://www.w3cplus.com/css/css-architecture.html)<br?
### 1.解耦
  通常，组件应该定义他们的外观如何，而不定义他们的布局或定位如何。所以当你在一条规则里面同时看到background，color，font，还有position，width，height，margin时，你就要小心咯。
  布局和定位应该要么由一个分离的布局类或是一个分离的容器元素处理（记住，为了高效地分离内容和表现，经常必不可少的将内容和他的容器分离）。
### 2.命名空间
  我们已经检查了为什么父类选择器不能100%高效的阻止样式的交叉污染。一个更好的办法是给类名本身应用命名空间。如果你r的元素是可视组件的一员，那么他的每一个子元素类都应该用组件的基类名作为他的命名空间。
### 4.扩展类
  当一个现有组件需要在一定的环境里看起来有点不同，创建一个修改类扩展他。
### 5.把css组织成逻辑结构
  Jonathan Snook在他写的一本很棒的书SMACSS中，提出可以把你的css分为4个不同的类别来组织,他们是基础样式，布局样式，模块样式以及状态样式。基础样式是由重置元素规则和元素默认样式组成。布局样式是定位站内元素以及通用布局就像网格系统。模块样式是可以复用的视觉元素，状态样式就是通过javascript涉及到开启或关闭。
