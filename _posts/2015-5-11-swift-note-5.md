---
layout: post
title: 清风注解 - Swift - 5 流程控制
---


### 流程控制

#### For 循环
* for-in 用来遍历一个区间（range），序列（sequence），集合（collection），系列（progression）里面所有的元素执行一系列语句。

	``` Swift
	for index in 1...5 {
    	println("\(index) times 5 is \(index * 5)")
	}
	// 1 times 5 is 5
	// 2 times 5 is 10
	// 3 times 5 is 15
	// 4 times 5 is 20
	// 5 times 5 is 25
	```
* for-in 中 index 是一个每次循环遍历开始时被自动赋值的常量。这种情况下，index在使用前不需要声明，只需要将它包含在循环的声明中，就可以对其进行隐式声明，而无需使用 let 关键字声明。
* for-in 中 index 常量只存在于循环的生命周期里。如果你想在循环完成后访问index的值，又或者想让index成为一个变量而不是常量，你必须在循环之前自己进行声明。
* 如果不需要知道区间内每一项的值，可以使用下划线`_`替代变量名来忽略对值的访问。

	``` Swift
	let base = 3
	let power = 10
	var answer = 1
	for _ in 1...power {
    	answer *= base
	}
	println("\(base) to the power of \(power) is \(answer)")
	// 输出 "3 to the power of 10 is 59049"
	```
* 使用for-in遍历一个数组所有元素。

	``` Swift
	let names = ["Anna", "Alex", "Brian", "Jack"]
	for name in names {
    	println("Hello, \(name)!")
	}
	// Hello, Anna!
	// Hello, Alex!
	// Hello, Brian!
	// Hello, Jack!
	```
* 可以通过遍历一个字典来访问它的键值对（key-value pairs）。遍历字典时，字典的每项元素会以(key, value)元组的形式返回，你可以在for-in循环中使用显式的常量名称来解读(key, value)元组。

	``` Swift
	let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
	for (animalName, legCount) in numberOfLegs {
    	println("\(animalName)s have \(legCount) legs")
	}
	// spiders have 8 legs
	// ants have 6 legs
	// cats have 4 legs
	```
* 字典元素的遍历顺序和插入顺序可能不同，字典的内容在内部是无序的，所以遍历元素时不能保证顺序。
* 可以使用for-in循环来遍历字符串中的字符（Character）。

	``` Swift
	for character in "Hello" {
    	println(character)
	}
	// H
	// e
	// l
	// l
	// o
	```
* for 条件递增（for-condition-increment）语句，用来重复执行一系列语句直到达成特定条件达成，一般通过在每次循环完成后增加计数器的值来实现。

	``` Swift
	for var index = 0; index < 3; ++index {
    	println("index is \(index)")
	}
	// index is 0
	// index is 1
	// index is 2
	```
* for 循环执行流程如下:
 1. 循环首次启动时，初始化表达式（initialization expression）被调用一次，用来初始化循环所需的所有常量和变量。
 2. 条件表达式（condition expression）被调用，如果表达式调用结果为false，循环结束，继续执行for循环关闭大括号 （}）之后的代码。如果表达式调用结果为true，则会执行大括号内部的代码（statements）。
 3. 执行所有语句（statements）之后，执行递增表达式（increment expression）。通常会增加或减少计数器的值，或者根据语句（statements）输出来修改某一个初始化的变量。当递增表达式运行完成后，重复执行第 2 步，条件表达式会再次执行。
* 在初始化表达式中声明的常量和变量只在 for 循环的生命周期里有效。如果想在循环结束后访问 index 的值，你必须要在循环生命周期开始前声明 index。

	``` Swift
	var index: Int
	for index = 0; index < 3; ++index {
    	println("index is \(index)")
	}
	// index is 0
	// index is 1
	// index is 2
	println("The loop statements were executed \(index) times")
	// 输出 "The loop statements were executed 3 times
	```

#### While 循环






#### 条件语句






#### 控制转移语句







-- End --
