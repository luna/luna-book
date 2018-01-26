# 基本的（数据类型）
本节把Luna中可用的基本数据类型走一遍。

将碰到一些常用的。

## 字面值
支持三种：特殊形式表达式、指示主要数据类型。

- Text：引号界定的字符序列
- Real：有小数点
- Int：没有小数点

创建字面值节点非常简单，只需要打开探测器、键盘敲出想要的值。

![][0]

牢记用户总是可以敲击<kbd>Tab</kbd>键，在选择制定类型的节点，带出探测器，得到该类型支持的所有操作的列表，包括相应的文档。

![][1]

## 数值类型
最基本的数值类型是Int和Real。

- Int：任意整型
- Real：任意浮点

**即将改变**

	目前，数值字面类型依据小数点来判定Int或Real。这意味着“1”是Int、“1.0”是Real。未来数值字面类型会是多态的，允许“1.7+2”这种表达式。

支持基本的算术操作和数学函数。

## 文本类型
不出所料，Luna文本类型就是Text。

支持两种文本：

- 解释的：单引号包裹，可以插入转义字符（如\n等）。
- 不解释的：双引号包裹，只支持唯一的转义字符“\"”。

默认采用单引号括起来的文本通常是足够便利的，除非需要包括很多特殊字符的文本。

**即将改变**

	未来“解释的”文本也允许插入任意表达式，先计算出表达式的结果，后把该结果放入文本中。例如：“"2加2的结果是`2+1`"”计算后是“"2加2的结果是4"”。

## 布尔类型
逻辑值用Bool来表示。有两个构造器：True和False。

支持基本逻辑操作：&&、||、not。

条件分支的最通用功能是“if...then...else”。

也可以更优雅的混合形式“if condition then True else False”。

该函数并无特别之处，所有参数都是标准数值并返回别的任何函数一样的值。

	def reportRelationshipToSeven x:
		relationship = if x > 7 then "greater than" else "less than or equal to"
		print (x.toText + " is " + relationship + "seven.")

## 列表和元组
最常用的容器。

列表时任意长度、包含相同类型值。例如“[3,4,5]”是List Int，“['first','second','thrid']”是List Text。标准库中还有一些有趣的函数和方法，返回想要形状的列表，在探测器中把可用的函数和方法过一遍。

	1.upto 5 # => [1,2,3,4,5]
	3.times "hello" #=> ["hello","hello","hello"]
	[True,False] . cycle . take 5 #=> [True,False,True,False,True]

元组和列表类似，但能存储不同类型的值且长度定义时就固定了。

	(1, "hello", False) :: (Int, Text, Bool)
	("hi", 3.0) :: (Text, Real)

**即将改变**

	未来列表和元组会合并为一种类型，完全理解其结构、允许自身长度信息、类型层次上不同元素。正如用户可能期望“["Hello",32,False]”这样的代码。

## 可能类型
和别的函数式语言不同，Luna没有null值。

这意味着，如果有个Int值，总是一个数值，没有成为无效数值的方法。

如果一个值可能不存在，就需要安全的方式编码。

此时Maybe闪亮登场！

可能类型的值必须是Just value或None。

可以通过模式匹配检查。

假定一个值是Maybe Int的变量myNumber，可以这样用：

	reportedValue = case myNumber of
		Just v -> 'Got a number ' + v.toText + '.'
		None -> 'Did not get a number.'
	print reportedValue

有一堆像“getWithDefault”一样有用的方法，大多数情况下很方便替代模式匹配。

查阅探测器获取更多详情。

---
[0]:./images/literals.png
[1]:./images/explorer-with-documents.png