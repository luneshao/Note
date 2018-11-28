# class

## 1.定义类

#### (1) 类声明

```javascript
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

tip: 类声明不会提升，需要先定义再使用。

#### (2) 类表达式

类表达式可以是被命名的或匿名的。赋予一个命名类表达式的名称是类的主体的本地名称。

```javascript
/* 匿名类 */ 
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};

/* 命名的类 */ 
let Rectangle = class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```

## 2.类体和方法体定义

#### 构造函数

`constructor`方法是一个特殊的方法，其用于创建和初始化使用`class`创建的一个对象。一个类只能拥有一个名为 “constructor”的特殊方法。

一个构造函数可以使用 `super` 关键字来调用一个父类的构造函数。

#### 静态方法

`static` 关键字用来定义一个类的一个静态方法。调用静态方法不需要实例化该类，但不能通过一个类实例调用静态方法。

静态方法通常用于为一个应用程序创建工具函数。

## 3.使用extends创建一个类的子类

如果子类中存在构造函数，则需要在使用“this”之前首先调用 `super()`。
