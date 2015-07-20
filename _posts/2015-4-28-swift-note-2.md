---
layout: post
title: 清风注解 - Swift - 2 基本运算符
tags: 
- 清风注解
---


### 基本运算符

#### 术语
* 运算符是检查、改变、合并值的特殊符号或短语。
* Swift 运算符有一元、二元和三元运算符。
* 一元运算符操作一个对象(有一个操作数)。分为前置运算符和后置运算符。
* 一元运算符必须紧跟操作对象。
* 二元运算符操作两个对象(有两个操作数)。它是中置运算符，放在两个操作对象之间。
* 三元运算符操作三个对象(有三个操作数)。Swift 只有一个三元运算符(`a?b:c`)。

#### 赋值运算符
* 赋值运算`a = b`，表示用 b 的值来初始化或更新 a 的值。
* 如果赋值运算符的右边是一个元组，它可以马上把元组的元素分解成多个常量或变量。

	``` Swift
	// 右侧元组被分解，并分别赋值给 x 和 y。现在 x 等于 1，y 等于 2。
	let (x, y) = (1, 2)
	```
* Swift 的赋值操作并不返回任何值。这个特性可以避免把`==`错误的写成`=`。

	``` Swift
	// 编译时 if 语句会报错，因为赋值语句(x = y)并不返回任何值。
	if x = y {
	}
	```

#### 算术运算符
* Swift 中所有的数值类型都支持基本的四则算术运算。
 * 加法 `+`
 * 减法 `-`
 * 乘法 `*`
 * 除法 `/`
* Swift 默认情况下不允许在数值运算中出现溢出情况。必须使用溢出运算符`&`来实现溢出运算。

	``` Swift
	let a: Int8 = 128
	let b: Int8 = 1
	let x: Int8 = a &+ b
	```
* 加法运算符可以用于字符串类型的拼接。

	``` Swift
	// newString 的拼接结果是“hello, world!”
	let newString = "hello, " + "world!"
	```
* 两个字符类型的值或字符类型的值和字符串类型的值相加会生成一个新的字符串类型的值。

	``` Swift
	let dog: Character = "d"
	let cow: Character = "c"
	// dogCow 拼接之后的值是“dc”
	let dogCow = dog + cow
	``` 
* 求余运算`a % b`是计算 a 除以 b，返回余数。
* 对于负数求余时，结果的符号会被忽略。
* Swift 可以对浮点数进行求余计算。

	``` Swift
	// 结果是一个 Double 类型的值 0.5。
	let value = 8 % 2.5
	``` 
* Swift 提供对变量本身加 1 或减 1 的自增`++`和自减`--`运算符。
* 自增和自减运算符操作的对象可以是整型和浮点型。
* 自增和自减运算符可以用作前置运算，也可以用作后置运算。++i，i++，--i，i--都是有效的写法。
* 自增和自减运算符既可以修改变量的值，也可以返回变量的值。
* 当使用返回值时，自增和自减运算符遵循以下原则：
 * 当 ++ 或 -- 前置时，先进行自增或自减操作，然后返回自增或自减后的值。
 * 当 ++ 或 -- 后置时，先返回其值，软后再进行自增或自减操作。

	``` Swift
	var a = 0
	// a 和 b 现在都是 1
	let b = ++a
	// a 现在是 2，c 是 a 自增之前的值 1
	let c = a++
	``` 
* 数值的正负号可以使用前缀`-`（即：一元负号）来切换。

	``` Swift
	let three = 3
	// minusThree 等于 -3
	let minusThree = -three
	// plusThree 等于 3
	let plusThree = -minusThree
	``` 
* 一元负号操作符和操作数之间不能用空格。
* 一元正号运算符`+`对操作数不做任何改变地返回操作数的值。

#### 复合赋值运算符
* Swift 提供其它运算符和赋值运算符组合的复合赋值运算符。
* 复合运算符`+=`是其中一种，下面的例子相当于 a = a + 2

	``` Swift
	var a = 1
	// 相当于 a = a + 2，现在 a 等于 3。
	a += 2
	``` 
* 复合运算符列表
 * `*=` 相乘和赋值 Multiply and assign
 * `/=` 相除和赋值 Divide and assign
 * `%=` 求余和赋值 Remainder and assign
 * `+=` 相加和赋值 Add and assign
 * `-=` 相减和赋值 Subtract and assign
 * `<<=` 向左位移和赋值 Left bit shift and assign
 * `>>=` 向右位移和赋值Right bit shift and assign
 * `&=` 按位与和赋值 Bitwise AND and assign
 * `^=` 按位异或和赋值 Bitwise XOR and assign
 * `|=` 按位或和赋值 Bitwise OR and assign
 * `&&=` 逻辑与和赋值 Logical AND and assign
 * `||=` 逻辑或和赋值 Logical OR and assign

#### 比较运算符
* Swift 的比较运算符比较两个操作数，并返回比较的布尔值结果。
* 比较运算符列表
 * 等于 `a == b`
 * 不等于 `a != b`
 * 大于 `a > b`
 * 小于 `a < b`
 * 大于等于 `a >= b`
 * 小于等于 `a <= b`
 * 恒等 `a === b`
 * 不恒等 `a !== b`
* 比较运算符多用于条件语句，如 if 条件。

	``` Swift
	if name = "jobs" {
		println("he is jobs")
	}
	else {
		println("he is cook")
	}
	``` 

#### 三元运算符
* 三元运算符的原型是`问题 ? 答案1 : 答案2`。它根据问题成立与否做出二选一的操作。如果`问题`成立，返回`答案1`的结果，如果不成立，返回`答案2`的结果。
* 三元运算符是以下代码的缩写形式

	``` Swift
	if question {
		answer1
	}
	else {
		answer2
	}
	``` 
* 过度使用三元运算符会使代码变的难懂，应避免在一个组合语句中使用多个三元运算符。

#### 空合并运算符
* 空合并运算符`a ?? b`，对可选类型 a 进行是否为空的判断，如果 a 不为空(包含一个值)就进行解封，否则就返回一个默认值 b。
* 空合并运算符有两个条件：
 * 表达式 a 必须是可选类型。
 * 默认值 b 的类型必须要和 a 的存储类型保持一致。
* 空合并运算符是以下代码的缩写形式

	``` Swift
	a != nil ? a! : b
	``` 

#### 区间运算符
* 闭区间运算符`a...b`：定义一个包含从 a 到 b(包括 a 和 b)的所有值的区间，b 必须大于 a。
* 闭区间运算符适用于迭代一个区间的所有值。

	``` Swift
	for index in 1...5 {
		println("\(index) * 5 = \(index * 5)")
	}
	// 输出结果如下：
	// 1 * 5 = 5
	// 2 * 5 = 10
	// 3 * 5 = 15
	// 4 * 5 = 20
	// 5 * 5 = 25
	``` 
* 半开区间运算符`a..<b`：定义一个从 a 到 b，但不包括 b 的区间。之所以称为半闭区间，是因为该区间包含第一个值而不包括最后一个值。
* 半开区间适用于遍历从 0 开始的列表（如数组）。

#### 逻辑运算符
* 逻辑运算符的操作对象是逻辑布尔值。
* Swift 支持的逻辑运算符：
 * 逻辑非`!a`
 * 逻辑与`a && b`
 * 逻辑或`a || b`
* 逻辑非运算对一个布尔值取反，它是一个前置运算符，且与操作数之间不能有空格。
* 逻辑与表示只有 a 和 b 的值都为 true 时，整个表达式的值才为 true。只要有一个值为 false，整个表达式的值就为 false。
* 逻辑与采用短路计算(short-circuit evaluation)，即如果第一个表达式的值为 false，将不再计算第二个表达式的值。
* 逻辑或表示两个逻辑表达式中有一个为 true 时，整个表达式的值就为 true。两个逻辑表达式都为 false 时，整个表达式的值才为 false。
* 逻辑或同样采用短路计算，即如果第一个表达式的值为 true，将不再计算第二个表达式的值。
* 在一个复杂表达式中，使用括号`()`来明确优先级，会使逻辑更明确。

	``` Swift
	let enteredDoorCode = true
	let passedRetinaScan = false
	let hasDoorKey = false
	let knowsOverridePassword = true
	if (enteredDoorCode && passedRetinaScan) ||
		hasDoorKey || knowsOverridePassword {
		println("Welcome!")
	}
	``` 

-- End --
