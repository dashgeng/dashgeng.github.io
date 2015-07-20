---
layout: post
title: 清风注解 - Swift - 3 字符串和字符
tags: 
- 清风注解
---


### 字符串和字符

#### 字符串字面量
* Swift 的`字符串 String`和`字符 Character`类型提供了一个快速的，兼容 Unicode 的方式来处理代码中的文本信息。
* 字符串和字符的连接操作只需要通过`+`将两个字符串或字符相连接即可。
* Swift 可以在常量、变量、字面量和表达式中进行字符串插值操作。
* 字符串字面量是由双引号 "" 包裹着的具有固定顺序的文本字符集。
* 字符串字面量可以为常量和变量提供初始值。

	``` Swift
	let someString = "Some string literal value"
	```
* 字符串字面量可以包含以下特殊字符：
 * 转义字符：空字符`\0`、反斜杠`\\`	、水平制表符`\t`、换行符`\n`、回车符`\r`、双引号`\"`、单引号`\'`。
 * Unicode 标量，写成`\u{n}`。u 为小写，n 为任意 1 到 8 位十六进制数。

	``` Swift
	let dollarSign = "\u{24}"
	```

#### 初始化空字符串
* 可以使用空字符串字面量`""`赋值给变量，也可以初始化一个新的 String 实例。

	``` Swift
	// 使用空字符串字面量`""`赋值给变量
	var emptyString = ""
	// 初始化一个新的 String 实例
	var anotherEmptyString = String()
	```
* 可以通过检查其布尔类型的 isEmpty 属性来判断该字符串是否为空。

	``` Swift
	if emptyString.isEmpty {
		println("这是一个空字符串")
	}
	```

#### 字符串可变性
* 将一个特定字符串分配给一个变量来对其进行修改。
* 将一个特定字符串分配给一个常量来保证其不会被修改。

	``` Swift
	var variableString = "Horse"
	// variableString 现在为 "Horse and carriage"
	variableString += "and carriage"
	let constantString = "Highlander"
	// 对常量进行修改会引起编译错误
	let constantString += "and another highlander"
	```

#### 字符串是值类型
* Swift 的 String 类型是值类型，而非引用类型。
* 创建一个新的字符串，相当于进行常量、变量的赋值操作。
* 在函数或方法中传递字符串时，会进行值拷贝。其传递的是字符串的值，而非字符串的引用。
* 在实际编译时，Swift 编译器会优化字符串的使用，使实际的复制只发生在绝对必要的情况下。

#### 使用字符
* Swift 的字符串类型表示特定序列的字符类型值的集合。
* Swift 的每一个字符值代表一个 Unicode 字符。
* 可以使用`for-in`循环来遍历字符串中每一个字符。

	``` Swift
	for character in "China" {
		println(character)
	}
	// character 循环遍历字符串“China”中每一个字符。
	```
* 通过标明`Character`类型注解，并通过字符字面量进行赋值，可以建立一个独立的字符常量或变量。

	``` Swift
	let yenSign: Character = "¥"
	```

#### 计算字符数量
* 通过调用全局 countElements 函数，并将字符串作为参数进行传递，可以获取该字符串的字符数量。

	``` Swift
	let unusualMenagerie = "Dog🐶"
	println("\(countElements(unusualMenagerie))")
	```
* 不同的 Unicode 字符以及相同 Unicode 字符的不同表示方式可能需要不同数量的内存空间来存储。所以 Swift 中的字符在一个字符串中并不一定占用相同的内存空间。

#### 连接字符串和字符
* 字符串通过加法运算符`+`相加在一起并创建一个新的字符串。

	``` Swift
	let string1 = "hello"
	let string2 = " there"
	// welcome 现在等于 “hello there”
	var welcome = string1 + string2
	```
* 可以通过加法赋值运算符`+=`将一个字符串添加到一个已经存在的字符串变量上。

	``` Swift
	var instruction = "look over"
	// instruction 现在等于 “look over there”
	instruction += string2
	```
* append 方法将一个字符附加到一个字符串变量的尾部。

	``` Swift
	let exclamationMark: Character = "!"
	// welcome.append 现在等于 “hello there!”
	welcome.append(exclamationMark)
	```
* Swift 中不能将一个字符串或字符添加到一个已经存在的字符变量上，因为字符变量只能包含一个字符。

#### 字符串插值
* 字符串插值是一种构建新字符串的方式，可以在其中包含常量、变量、字面量、表达式。
* 字符串插值中的字符串字面量被包裹在以反斜杠为前缀的圆括号中。

	``` Swift
	let multiplier = 3
	// message 的值是 “3 乘以 2.5 是 7.5”
	let message = "\(multiplier) 乘以 2.5 是 \(Double(multiplier) * 2.5)"
	```
* 串插值字符串中写在括号内的表达式不能包含非转义双引号`"`和反斜杠`\`，也不能包含回车或换行符。

#### 比较字符串
* Swift 提供了三种方式来比较字符串的值：字符串相等，前缀相等和后缀相等。
* 字符串相等：如果两个字符串以同一顺序包含完全相同的字符，则认为两个字符串相同。

	``` Swift
	let quotation = "同一个世界，同一个梦想！"
	let sameQuotation = "同一个世界，同一个梦想！"
	if quotation == sameQuotation {
		println("这两个字符串相等")
	}
	```
* 通过调用字符串的`hasPrefix`或`hasSuffix`方法来检查字符串是否拥有特定的前缀或后缀。

	``` Swift
	let wordList = [
		"dash",
		"death",
		"door",
		"doom",
		"duty"]
	for word in wordList {
		if word.hasPrefix("doo") {
			println(word)
		}
	}
	for word in wordList {
		if word.hasSuffix("h") {
			println(word)
		}
	}
	```

#### 字符串大小写
* Swift 中通过字符串的`uppercaseString`和`lowercaseString`属性来访问大写和小写版本的字符串。

	``` Swift
	import Foundation
	let normal = "Could you help me ,please?"
	// shouty 现在的值是 "COULD YOU HELP ME ,PLEASE?"
	let shouty = normal.uppercaseString
	// whispered 现在的值是 "could you help me ,please?"
	let whispered = normal.lowercaseString
	```
#### Unicode
* Swift 中可以利用 for-in 来对字符串进行遍历，从而以Unicode字符的方式访问每一个字符值。

	``` Swift
	let dogString = "Dog!🐶"
	for codeUnit in dogString {
		print("\(codeUnit)")
	}
	print("\n")
	// 输出结果: Dog!🐶
	```
* Swift 中能够以其它三种 Unicode 兼容的方式访问字符串的值。
 * UIF-8 代码单元集合：利用字符串的 utf8 属性进行访问
 
	``` Swift
	let dogString = "Dog!🐶"
	for codeUnit in dogString.utf8 {
		print("\(codeUnit)")
	}
	print("\n")
	// 输出结果: 68 111 103 33 240 159 144 182
	// 其中 68 111 103 33 代表 Dog!，240 159 144 182 代表 🐶
	```
 * UIF-16 代码单元集合：利用字符串的 utf16 属性进行访问
 
	``` Swift
	let dogString = "Dog!🐶"
	for codeUnit in dogString.utf16 {
		print("\(codeUnit)")
	}
	print("\n")
	// 输出结果: 68 111 103 33 55357 56374
	// 其中 68 111 103 33 代表 Dog!，55357 56374 代表 🐶
	```
 * 21 位的 Unicode 标量值集合：利用字符串的 unicodeScalars 属性进行访问
 
	``` Swift
	let dogString = "Dog!🐶"
	for codeUnit in dogString {
		print("\(codeUnit)")
	}
	print("\n")
	// 输出结果: 68 111 103 33 1285054
	// 其中 68 111 103 33 代表 Dog!，1285054 代表 🐶
	```

-- End --
