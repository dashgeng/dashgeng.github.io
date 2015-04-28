---
layout: post
title: 清风注解 - Swift - 2 基本运算符
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
	if x = y 
	{
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

#### 三目运算符

#### 空合运算符

#### 区间运算符

#### 逻辑运算符

-- End --