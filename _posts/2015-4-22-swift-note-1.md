---
layout: post
title: 清风注解 - Swift - 1
---


### 基础知识

#### 常量和变量
* `常量`和`变量`把一个名字和一个指定类型的值关联起来。
* 常量的值一旦设定就不能改变，而变量的值可以随意更改。
* 选择常量还是变量：将不需要改变的值设置为常量，将需要改变的值设置为变量。
* 常量和变量的使用原则是：先声明，后使用。
* 用 `let` 声明常量。

	``` Swift
	let pi = 3.141592654
	```

* 用 `ver` 声明变量。

	``` Swift
	var currentTime = "12:06"
	```
* 在一行中可以同时声明多个常量或变量，之间用逗号`，`隔开。

	``` Swift
	let a = 3, b = 4, c = 5
	var x = 10, y = 20, z = 15
	```
* 在声明常量或变量时可以加上`类型标注(type annotation)`，说明常量或变量中要存储的值的类型。
* 类型标注的添加方法是：在常量或变量名后面加上一个`冒号`和`空格`，然后加上`类型名称`。

	``` Swift
	let Name: String
	var Height: Int
	```
* 一般很少需要写类型标注，如果在声明常量或变量时赋了一个初始值，Swift 可以通过`类型推断 （type inference）`，自动推断出这个常量或变量的类型。
* 常量和变量的命名可以包括 Unicode 字符。

	``` Swift
	var π = "pi"
	var 🐶 = "dog"
	var 中国 = "china"
	```
* 常量和变量的命名不能包含数学符号，箭头，保留的（或者非法的）Unicode 码位，连线与制表符。
* 常量和变量的命名不能以数字开头，但是可以在常量与变量名的其他地方包含数字。
* 常量和变量的作用域内，不能使用相同的名字再次进行声明。
* 常量和变量的类型一旦确定，就不能改变。
* 常量和变量不能进行相互转换。
* 如果需要使用与 Swift 保留关键字相同的名称作为常量或变量名，可以使用`反引号` ` 将关键字包围的方式将其作为名字使用。
* 只能使用相同类型的值改变原有变量值。
* 可以使用 `println` 函数输出当前常量或变量的值。

	``` Swift
	println(currentTime)
	```
* `print` 函数同样可以输出内容，与 println 唯一的区别是在输出内容最后不会换行。

	``` Swift
	println("My name is DashGeng. What's your name? ")
	```
* Swift 用`字符串插值(string interpolation)`的方式把常量名或变量名当作占位符加入到长字符串中，Swift 会用当前常量或变量值替换这些占位符。
* 字符串插值的写法：将常量或变量名放入`圆括号 ( )`中，并在开括号前使用`反斜杠 \`将其转义。

	``` Swift
	println("The time now is \(currentTime).")
	```

#### 注释
* 单行注释以`正双斜杠 //`作为起始标记。

	``` Swift
	// 这是一个单行注释。
	```
* 多行注释块起始标记为`一个正斜杠后跟一个星号`(`/*`)，终止标记为`一个星号后跟一个正斜杠`(`*/`)。

	``` Swift
	/* 
	   这是一个
	   多行注释块。
	*/
	```
* 多行注释块中可以嵌套多行注释块和单行注释。

	``` Swift
	/* 
	   这是一个
	   多行注释块。
	   // 嵌套一个单行注释。
	   /* 嵌套一个
	      多行注释块。 */
	*/
	```

#### 分号
* Swift 不强制要求每条语句的结尾处使用`分号 ;`，你也可以按照自己的习惯添加分号。
* 一种特殊的情况是：当一行内写多条语句时，必须在前一个语句的结尾处添加分号。

	``` Swift
	let userEmail = "dashgeng@163.com"; println("my email is \(userEmail).")
	```

#### 整数
* Swift 提供了8, 16, 32, 64位的有符号和无符号整数类型。
* 有符号整数类型：Int8, Int16, Int32, Int64。
* 无符号整数类型：UInt8, Uint16, Uint32, Uint64。
* 整数类型的最大值和最小值可以使用`max`和`min`属性取得。

	``` Swift
	// minValue 为 0。
	let minValue = UInt8.min
	// maxValue 为 255。
	let maxValue = UInt8.max
	```
* Swift 提供了一个特殊的整数类型`Int`，长度与当前平台的原生字长相同：
 * 在32位平台上，Int 和 Int32 长度相同。
 * 在64位平台上，Int 和 Int64 长度相同。
* Swift 也提供了一个特殊的无符号整数类型`UInt`，长度与当前平台的原生字长相同：
 * 在32位平台上，UInt 和 UInt32 长度相同。
 * 在64位平台上，UInt 和 UInt64 长度相同。
* 尽量不要使用 UInt，而使用 Int。统一使用 Int 可以提高代码的可复用性，避免不同类型数字之间的转换，并且匹配数字的类型推断。

#### 浮点数
* Swift 提供了表示32位浮点数的`Float`和表示64位浮点数的`Double`。
* Float 至少有6位数字，Double 至少有15位数字。

#### 类型安全和类型推断
* Swift 是一个类型安全 (type safe) 的语言。它会在编译代码时进行类型检查 (type checks)，并把不匹配的类型标记为错误。
* 没有显示指定类型的常量，变量或表达式在编译代码时，Swift 会使用类型推断自动推断出它的类型。
* 声明常量或变量并赋给它们一个`字面量(literal value)`(初值)时，即可触发类型推断。

	``` Swift
	// myAge 会被断测为 Int 类型
	let myAge = 32
	// pi 会被推断为 Double 类型
	let pi = 3.14159
	// anotherPi 会被推断为 Double 类型。
	let anotherPi = 3 + 0.14159
	```
* Swift 类型推断规则：
 * 整型字面量总是被推断为 Int 类型。 
 * 浮点型字面量总是被推断为 Double 类型。
 * 如果表达式中同时出现了整数和浮点数，会被推断为 Double 类型。

#### 数值型字面量
* 数值字面量分为：整数字面量和浮点字面量。
* 整数字面量有四种：
 * 十进制数，没有前缀
 * 二进制数，前缀是`0b`
 * 八进制数，前缀是`0o`
 * 十六进制数，前缀是`0x`

	``` Swift
	// 十进制数 17
	let decimalInteger = 17
	// 二进制数 17
	let binaryInteger = 0b10001
	// 八进制数 17
	let octalInteger = 0o21
	// 十六进制数 17
	let hexadecimalInteger = 0x11
	``` 
* 浮点字面量有两种：
 * 十进制数，没有前缀
 * 十六进制数，前缀是`0x`
* 浮点字面量小数点两边必须至少各有一个十进制(或十六进制)数字。
* 浮点字面量还有一个可选的指数(exponent)。
 * 十进制数的指数通过`E`或`e`指定。
 * 十六进制数的指数通过`P`或`p`指定。
 
	``` Swift
	// 十进制数 12.1875
	let decimalDouble = 12.1875
	// 十进制指数形式 12.1875
	let exponentDouble = 1.21875e1
	// 十六进制指数形式 12.1875
	let hexadecimalDouble = 0xC.3p0
	``` 

#### 数值型类型转换
* 不同类型的变量和常量可以存储不同范围的数字，如果数字超出了可存储的范围，编译时会报错。
* 要将一种数字类型转换成另一种，就要用当前值来初始化一个期望类型的新数字。

	``` Swift
	let valueInt8: Int8 = 127
	let valueInt16: Int16 = Int16(valueInt8)
    ```
* 表达式中不同类型的常量和变量必须显式转换为相同类型才能计算。

	``` Swift
	let towThousand: UInt16 = 2_000
	let one: UInt8 = 1
	let towThousandAndOne = towThousand + UInt16(one)
    ```
* 浮点数到整数的转换中，浮点值会被截取。
* 计算表达式时，数字字面量可以直接与任意类型的值相结合，而无需显式转换类型。因为数字字面量本身没有明确的类型，它们的类型会被自动推断。

	``` Swift
	let count: Int16 = 500
	let total: Int16 = count + 1
    ```

#### 类型别名
* 类型别名(type aliases)就是给现有类型定义另一个名字。使用`typealias`关键字来定义类型别名。

	``` Swift
	typealias AudioSample = UInt16
    ```
* 定义了一个类型别名之后，你可以在任何使用原始类型名称的地方使用别名。

	``` Swift
	var maxAmplitudeFound = AudioSample.min
    ```

#### 布尔型
* 布尔(Boolean)类型是 Swift 的基本数据类型。使用`Bool`关键字来定义。
* 布尔值是指逻辑上的真或假。Swift 用`true`代表真值，`false`代表假值。

	``` Swift
	var isCancel: Bool = false
	isCancel = true
	```
* Swift 中，如果在需要使用 Bool 类型的地方使用了非布尔值，Swift 的类型安全机制会报错。
	
#### 元组
* 元组(tuples)把多个值组合成一个复合值。元组内的值可以是任意类型，并不要求是相同类型。

	``` Swift
	// http404Error 的类型是 (Int, String)，值是 (404, "Not Found")
	let http404Error = (404, "Not Found")
	```
* 可以将元组的内容分解(decompose)成单独的常量和变量。

	``` Swift
	let (statusCode, statusMessage) = http404Error
	// 输出 "The status code is 404"
	println("The status code is \(statusCode)")
	// 输出 "The status message is Not Found"
	println("The status message is \(statusMessage)")
	```
* 如果只需要一部分元组值，分解时可以把要忽略的部分用下划线`_`标记。

	``` Swift
	let (justTheStatusCode, _) = http404Error
	// 输出 "The status code is 404"
	println("The status code is \(justTheStatusCode)")
	```
* 元组中的元素可以通过下标来访问，下标从`0`开始。

	``` Swift
	// 输出 "The status code is 404"
	println("The status code is \(http404Error.0)")
	// 输出 "The status message is Not Found"
	println("The status message is \(http404Error.1)")
	```
* 在定义元组时可以给单个元素命名，之后可以通过元素名称来获取或设置这些元素的值。

	``` Swift
	var http200Status = (statusCode: 200, description: "OK")
	// 输出 "The status code is 200"
	println("The status code is \(http200Status.statusCode)")
	// 输出 "The status message is OK"
	println("The status message is \(http200Status.description)")
	// 使用元素名称改变元素的值
	http200Status.statusCode = 300
	// 输出 "The status code is 300"
	println("The status code is \(http200Status.statusCode)")
	```
* 元组适合在临时组织值时使用，其并不适合创建复杂的数据结构。如果要创建的数据结构并不是临时使用，请使用类或结构体创建，而不是使用元组。

#### 可选
* 可选类型(optionals)用来处理值可能缺失的情况。
* 可选类型表示：有值，等于 x；或者没有值
* 可选类型写作`类型?`，例如：Int?。问号暗示包含的值是可选类型，也就是说可能包含值，也可能不包含值。
* 使用`if`语句可以用来判断一个可选是否包含值。如果可选类型有值，结构为 true；如果没有值，结果为 false。
* 当确定可选类型包含值后，可以在可选名字后面加一个`感叹号 !`来获取值。这被称作可选值的强制解析。

	``` Swift
	let possibleNumber = "123"
	// toInt() 返回可选类型 Int?
	let convertedNumber = possibleNumber.toInt()
	if convertedNumber != nil 
	{
	    println("\(possibleNumber) has an integer value of \(convertedNumber!)")
	}
	```
* 使用可选绑定(optional binding)来判断可选类型是否包含值，如果包含就把值赋给一个临时常量或变量。
* 可选绑定可以用在`if`和`while`语句中。

	``` Swift
	if let actualNumber = possibleNumber.toInt() 
	{
	    println("\(possibleNumber) has an integer value of \(actualNumber)")
	}
	```
* 可以使用 nil 给可选变量赋值，用来表示它没有值。
* nil 不能用于非可选常量或变量。
* 声明可选常量或变量时，如果没有赋值，Swift 会把常量或变量的值设置为 nil。

	``` Swift
	// surveyAnswer 被自动设置为 nil
	var surveyAnswer: String?
	```
* 在 Swift 中 nil 不是指针，它是一个确定的值，用来表示值的缺失。任何类型的可选状态都可以被设置为 nil。
* 如果一个可选类型的常量或变量在第一次被赋值之后，总会有值。可以声明成隐式解析可选类型，写作`类型!`，例如：Int!。
* 隐式解析可选类型在使用时，无需在变量名之后加`感叹号 !`，它可以被当做非可选类型来使用，不需要每次使用解析来获取可选值。

	``` Swift
	let assumedString: String! = "An implicitly unwrapped optional string."
	// 不需要使用感叹号
	println(assumedString)
	```
* 如果一个变量在使用中可能变成 nil 的话，请不要使用隐式解析可选类型。

#### 断言



-- End --
