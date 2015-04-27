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

#### 元组

#### 可选

#### 断言



-- End --
