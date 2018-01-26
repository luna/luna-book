# 自定义（数据类型）

## 类和对象
对象是把数据和行为绑定在一起的基本块。

Luna的绑定方法结合面向对象语言已知的途径、纯函数式编程技术，比如代数数据类型（Algebraic Data Type）。

### 简介
Luna中类的概念和大多数已知的编程语言不同。

如果读者熟悉Java或Python，一定会惊讶。

首先，Luna对象，除了包含多个字段（域），还引入多种卓著的风味。已知的函数式编程的代数数据类型和用多个构造器（每个构造器定义不同结构）当中的一个来构建对象的基本含义。

采用这钟技术，可是说任何Shape是一个Circle或Rectangle。

给定类型为Shape的对象，总是需要用模式匹配来发觉究竟是哪钟绝体类型。

然而，感谢方法，不论用哪种构造器，总可以调用一些行为。

意味着给定一个Shape类型值，总是可以用它的area方法，即使不知道用的哪个构造器。

不变性是Luna对象的另一个重要特点。

可能在别的编程语言中用过可变对象和表达式如“counter.count += 1”。

在Luna中，每个对象都是不可变的：一旦以某种方式创建完成，永远不能改变。

如果写“foo = Circle 15.0”，变量foo总是保持有相同半径（15.0)的Circle，不论如何使用。

任何可能改变对象的方法，实际上返回被修改过的版本。

所以如果有个列表，调用它的sort方法，原始的列表保持sort之前的状态，而是从sort方法返回整理过的列表，需要把这个新的列表分配给另外的变量（如果后边想用这个整理过的列表）。

### 类定义
**即将改变**

	眼下，在可视化编辑器中没法定义类及其方法。本节描述的机制都用来读的，很快就会支持。

用class关键字定义类，随后是构造器和方法。

用Shape类的定义来说明一下：

	class Shape:
		Circle:
			radius :: Real
		Rectangle:
			width :: Real
			height :: Real

		def perimeter: case self of
			Circle r: 2.0 * pi * r
			Rectangle w h: 2.0 * w + 2.0 * h

		def area: case self of
			Circle r: pi * r * r
			Rectangle w h: w * h

上述代码的第一部分片段定义构造器。

不同对象的构造器不同。

因此第一部分定义声明“一个Shape要么是Circle要么是Rectangle”。

然后定义一些方法。

方法就像函数，但是有个隐含的参数“self”。

方法通过“.”操作符调用，方法定义内的话，之前的就是“self”。

上述定义的两个方法片段都用了模式匹配（case），允许基于某些对象的构造器修改行为。

也可以“Circle 2.0 . area”来是使用新定义的类。

### 构造器
大多数Luna类都有至少一个构造器。

用来创建类的实例以及对象的模式匹配。

定义构造器的基本方式：

	class Shape:
		Circle:
			center :: Point
			radius :: Real
		Rectangle:
			topLeft :: Point
			bottomRight :: Point

上述片段定义一个Shpae类及其两个构造器：Circle和Rectangle。

每个构造器保存给定形状的基本信息。

可以省略字段（域）名，放在代码中如下：

	class Shape:
		Circle Point Real
		Rectangle Point Point

此时代码已经十分简洁，却又缺点。

不知道定义的字段是什么含义；不能通过字段名访问之。

**即将改变**

	目前，当只给出一个明确的构造器时，Luna允许通过字段名访问之。该行为很快会扩展来兼容多个构造器的类。

最后，当只有一个构造器时，可以跳过字段名。

下面例子中，Luna将会创建一个以类名为名的构造器。

	class Vector:
		x y z :: Real

## 构造器和模式匹配
类关联构造器有两个重要角色：

- 提供创建给定类对象的一种途径。
- 当作模式用来判定使用哪个构造器创建的泪对象并访问其字段。

### 对象构造
构造函数可以当作普通函数来用。

需要参数值初始化字段（以声明的顺序）并返回给定类的对象。

	class Maybe a:
		Just a
		Nothing

提供多达两个这样的值：

	Just :: a -> Maybe a
	Nothing :: Maybe a

![][0]

注意：**因为Nothing构造器没有字段，就不是个函数，是个常量，假定类型Maybe a是任何选择的a**。

### 模式匹配
允许把对象解包成构成自身的字段，假定模式匹配中使用的构造器和分配给该对象的构造器是一样的。

先用左手边的分配操作符的模式，分配字段值给模式提到的变量。

一起看看Vector类如何做模式匹配的。

	class Vector:
		x y z :: Real

	myVec = Vector 1.0 2.0 3.0
	Vector a b c = myVec
	bTimeOne = b * 1.0

![][1]

仔细跟踪构造器，假定选择右边的构造器且导致一个不匹配的运行时错误。

作为经验法则（rule of thumb），应该仅在有一个构造器的类上运用这种形式的模式匹配。

### Case表达式
控制模式识别的最通用方式。

有疑问时通常也是最安全的。

经常需要依靠这种模式识别的方式。

这是一种允许判定对象用哪个构造器创建的机制，每种可能给出不同值。

回顾Shape类，假定手里有渲染Circle和Rectangle的设备且需要渲染一般的Shape对象。

可以按如下简单的Case表达式完成：

	def render shape:
		case shape of
			Circle c r: drawCircle c r
			Rectangle tl br: drawRectangle tl br

结构非常明确：

- 在“case...of”之间需要提供需要判定身份的对象。
- 提供一系列从句，每条返回值用于特定构造器场景。

## 多态机制

### 类型参数
Luna类也可以提供类型参数，某些值让自身多态。

	class Vector:
		x y z :: Real

假使需要一个Int的Vector会怎样？

当前的方法，只是针对这个目的，可以要求创建另外的类。

然而，给Vector类添加类型参数：

	class Vector a:
		x y z :: a

装备了这种定义，可以创建包含任何类型元素的Vector。

	Vector "hello" "world" "!" :: Vector Text
	Vector 1 2 3 :: Vector Int
	Vector 1.0 2.0 3.0 :: Vector Real

![][2]

### Constrained方法
也可能实现一些类型a假定的额外方法属性（例如支持算术运算或定义若干别的方法）。

一旦使用这些属性，Luna类型检查器自动持续追踪之，并检查是否安全。

	class Vector a:
		x y z :: a
		def dotProduct that:
			self.x * that.x + self.y * that.y + self.z * that.z

这个dotProduct方法对任何支持加法和乘法的元素有用，Int或Real自然没问题，Text的话就要报类型错误。

	Vector 1 2 3 . dotProduct (Vector 4 5 6) # 返回32::Int
	Vector 1.0 2.0 3.0 . dotProduct (Vector 4.0 5.0 6.0) # 返回32.0::Real
	Vector "hello" "world" "!" . dotProduct (Vector "foo" "bar" "baz") # 不会编译

![][3]

---
[0]:./images/just-constructor-applied-with-types.png
[1]:./images/inline-pattern.png
[2]:./images/polymorphic-vectors.png
[3]:./images/vector-dot-product.png