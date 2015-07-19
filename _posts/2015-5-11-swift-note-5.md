---
layout: post
title: 清风注解 - Swift - 5 流程控制
tags: 
- Swift
- 清风注解
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
* while 循环运行一系列语句直到条件变成 false。这类循环适合使用在第一次迭代前迭代次数未知的情况下。
 * while 循环，每次在循环开始时计算条件是否符合
 * do-while 循环，每次在循环结束时计算条件是否符合
* while 循环从计算单一条件开始。如果条件为 true，会重复运行一系列语句，直到条件变为 false。

	``` Swift
	var square = 0
	var diceRoll = 0
	while square < finalSquare {
    	// 掷骰子
    	if ++diceRoll == 7 { diceRoll = 1 }
    	// 根据点数移动
    	square += diceRoll
    	if square < board.count {
    	    // 如果玩家还在棋盘上，顺着梯子爬上去或者顺着蛇滑下去
    	    square += board[square]
    	}
	}
	println("Game over!")
	```
* do-while 循环是在判断循环条件之前，先执行一次循环的代码块，然后重复循环直到条件为 false。

	``` Swift
	do {
    	// 顺着梯子爬上去或者顺着蛇滑下去
    	square += board[square]
    	// 掷骰子
    	if ++diceRoll == 7 { diceRoll = 1 }
    	// 根据点数移动
    	square += diceRoll
	} while square < finalSquare
	println("Game over!")
	```

#### 条件语句
* Swift 提供两种类型的条件语句：if 语句和 switch 语句。通常，当条件较为简单且可能的情况很少时，使用 if 语句。而 switch 语句更适用于条件较复杂、可能情况较多且需要用到模式匹配（pattern-matching）的情境。
* if 语句最简单的形式就是只包含一个条件，当且仅当该条件为 true 时，才执行相关代码。

	``` Swift
	var temperatureInFahrenheit = 30
	if temperatureInFahrenheit <= 32 {
    	println("It's very cold. Consider wearing a scarf.")
	}
	// 输出 "It's very cold. Consider wearing a scarf."
	```
* if 语句允许二选一，也就是当条件为 false 时，执行 else 语句。

	``` Swift
	temperatureInFahrenheit = 40
	if temperatureInFahrenheit <= 32 {
    	println("It's very cold. Consider wearing a scarf.")
	} else {
    	println("It's not that cold. Wear a t-shirt.")
	}
	// 输出 "It's not that cold. Wear a t-shirt."
	```
* 可以把多个 if 语句链接在一起使用。

	``` Swift
	temperatureInFahrenheit = 90
	if temperatureInFahrenheit <= 32 {
    	println("It's very cold. Consider wearing a scarf.")
	} else if temperatureInFahrenheit >= 86 {
    	println("It's really warm. Don't forget to wear sunscreen.")
	} else {
    	println("It's not that cold. Wear a t-shirt.")
	}
	// 输出 "It's really warm. Don't forget to wear sunscreen."
	```
* 多个 if 语句链接在一起使用时，最后的 else 语句是可选的。

	``` Swift
	temperatureInFahrenheit = 72
	if temperatureInFahrenheit <= 32 {
    	println("It's very cold. Consider wearing a scarf.")
	} else if temperatureInFahrenheit >= 86 {
    	println("It's really warm. Don't forget to wear sunscreen.")
	}
	```
* switch 语句会尝试把某个值与若干个模式（pattern）进行匹配。根据第一个匹配成功的模式，switch 语句会执行对应的代码。当有可能的情况较多时，通常用 switch 语句。
* switch 语句都由多个 case 构成。每一个 case 都是代码执行的一条分支，switch 语句会决定哪一条分支应该被执行。
* switch语句必须是完备的，每一个可能的值都必须至少有一个 case 分支与之对应。
* 在某些不可能涵盖所有值的情况下，你可以使用默认（default）分支满足该要求，这个默认分支必须在switch 语句的最后面。

	``` Swift
	let someCharacter: Character = "e"
	switch someCharacter {
	case "a", "e", "i", "o", "u":
    	println("\(someCharacter) is a vowel")
	case "b", "c", "d", "f", "g", "h", "j", "k", "l", "m",
	"n", "p", "q", "r", "s", "t", "v", "w", "x", "y", "z":
    	println("\(someCharacter) is a consonant")
	default:
    	println("\(someCharacter) is not a vowel or a consonant")
	}
	// 输出 "e is a vowel"
	```
* 在 Swift 中，当匹配的 case 分支中的代码执行完毕后，程序会终止 switch 语句，而不会继续执行下一个 case 分支。这也就是说，不需要在 case 分支中显式地使用break语句。这使得switch语句更安全、更易用，也避免了因忘记写break语句而产生的错误。
* 每一个 case 分支都必须包含至少一条语句。这就避免了意外地从一个 case 分支贯穿到另外一个，使得代码更安全、也更直观。
* 一个 case 也可以包含多个模式，用逗号把它们分开（如果太长了也可以分行写）。

	``` Swift
	switch some value to consider {
	case value 1,
		value 2:
		statements
	}
	```
* case 分支的模式也可以是一个值的区间。

	``` Swift
	let count = 3_000_000_000_000
	let countedThings = "stars in the Milky Way"
	var naturalCount: String
	switch count {
	case 0:
    	naturalCount = "no"
	case 1...3:
    	naturalCount = "a few"
	case 4...9:
	    naturalCount = "several"
	case 10...99:
	    naturalCount = "tens of"
	case 100...999:
	    naturalCount = "hundreds of"
	case 1000...999_999:
	    naturalCount = "thousands of"
	default:
	    naturalCount = "millions and millions of"
	}
	println("There are \(naturalCount) \(countedThings).")
	// 输出 "There are millions and millions of stars in the Milky Way."
	```
* 可以使用元组在同一个 switch 语句中测试多个值。元组中的元素可以是值，也可以是区间。另外，使用下划线`_`来匹配所有可能的值。

	``` Swift
	let somePoint = (1, 1)
	switch somePoint {
	case (0, 0):
	    println("(0, 0) is at the origin")
	case (_, 0):
	    println("(\(somePoint.0), 0) is on the x-axis")
	case (0, _):
	    println("(0, \(somePoint.1)) is on the y-axis")
	case (-2...2, -2...2):
	    println("(\(somePoint.0), \(somePoint.1)) is inside the box")
	default:
	    println("(\(somePoint.0), \(somePoint.1)) is outside of the box")
	}
	// 输出 "(1, 1) is inside the box"
	```
* Swift 允许多个 case 匹配同一个值。如果存在多个匹配，那么只会执行第一个被匹配到的 case 分支。剩下的能够匹配的 case 分支都会被忽略掉。
* case 分支的模式允许将匹配的值绑定到一个临时的常量或变量，这些常量或变量在该 case 分支里就可以被引用了——这种行为被称为值绑定（value binding）。

	``` Swift
	let anotherPoint = (2, 0)
	switch anotherPoint {
	case (let x, 0):
	    println("on the x-axis with an x value of \(x)")
	case (0, let y):
	    println("on the y-axis with a y value of \(y)")
	case let (x, y):
	    println("somewhere else at (\(x), \(y))")
	}
	// 输出 "on the x-axis with an x value of 2"
	```
* switch 语句不包含默认分支。
* case 分支的模式可以使用where语句来判断额外的条件。

	``` Swift
	let yetAnotherPoint = (1, -1)
	switch yetAnotherPoint {
	case let (x, y) where x == y:
	    println("(\(x), \(y)) is on the line x == y")
	case let (x, y) where x == -y:
	    println("(\(x), \(y)) is on the line x == -y")
	case let (x, y):
	    println("(\(x), \(y)) is just some arbitrary point")
	}
	// 输出 "(1, -1) is on the line x == -y"
	```

#### 控制转移语句
* 控制转移语句改变你代码的执行顺序，通过它你可以实现代码的跳转。Swift 有四种控制转移语句。
 * continue
 * break
 * fallthrough
 * return
* continue语句告诉一个循环体立刻停止本次循环迭代，重新开始下次循环迭代。

	``` Swift
	let puzzleInput = "great minds think alike"
	var puzzleOutput = ""
	for character in puzzleInput {
	    switch character {
	    case "a", "e", "i", "o", "u", " ":
        continue
	    default:
	        puzzleOutput.append(character)
	    }
	}
	println(puzzleOutput)
    // 输出 "grtmndsthnklk"
	```
* break 语句会立刻结束整个控制流的执行。当你想要更早的结束一个 switch 代码块或者一个循环体时，你都可以使用 break 语句。
* 当在一个循环体中使用break时，会立刻中断该循环体的执行，然后跳转到表示循环体结束的大括号`}`后的第一行代码。不会再有本次循环迭代的代码被执行，也不会再有下次的循环迭代产生。
* 当在一个switch代码块中使用break时，会立即中断该switch代码块的执行，并且跳转到表示switch代码块结束的大括号`}`后的第一行代码。这种特性可以被用来匹配或者忽略一个或多个分支。

	``` Swift
	let numberSymbol: Character = "三"  // 简体中文里的数字 3
	var possibleIntegerValue: Int?
	switch numberSymbol {
	case "1", "١", "一", "๑":
	    possibleIntegerValue = 1
	case "2", "٢", "二", "๒":
	    possibleIntegerValue = 2
	case "3", "٣", "三", "๓":
	    possibleIntegerValue = 3
	case "4", "٤", "四", "๔":
	    possibleIntegerValue = 4
	default:
	    break
	}
	if let integerValue = possibleIntegerValue {
	    println("The integer value of \(numberSymbol) is \(integerValue).")
	} else {
	    println("An integer value could not be found for \(numberSymbol).")
	}
	// 输出 "The integer value of 三 is 3."
	```
* 如果你确实需要 C 风格的贯穿（fallthrough）的特性，可以在每个需要该特性的 case 分支中使用 fallthrough 关键字。

	``` Swift
	let integerToDescribe = 5
	var description = "The number \(integerToDescribe) is"
	switch integerToDescribe {
	case 2, 3, 5, 7, 11, 13, 17, 19:
	    description += " a prime number, and also"
	    fallthrough
	default:
	    description += " an integer."
	}
	println(description)
	// 输出 "The number 5 is a prime number, and also an integer."
	```
* fallthrough 关键字不会检查它下一个将会落入执行的 case 中的匹配条件。fallthrough 简单地使代码执行继续连接到下一个 case 中的执行代码。
* 可以使用标签来标记一个循环体或者 switch 代码块，当使用 break 或者 continue 时，带上这个标签，可以控制该标签代表对象的中断或者执行。
* 产生一个带标签的语句是通过在该语句的关键词的同一行前面放置一个标签，并且该标签后面还需带着一个冒号。

	``` Swift
	gameLoop: while square != finalSquare {
    	if ++diceRoll == 7 { diceRoll = 1 }
    	switch square + diceRoll {
    	case finalSquare:
        	// 到达最后一个方块，游戏结束
        	break gameLoop
    	case let newSquare where newSquare > finalSquare:
        	// 超出最后一个方块，再掷一次骰子
        	continue gameLoop
    	default:
        	// 本次移动有效
        	square += diceRoll
        	square += board[square]
    	}
	}
	println("Game over!")
	```

-- End --
