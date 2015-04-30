---
layout: post
title: 清风注解 - Swift - 4 集合类型
---


### 集合类型
* Swift 中数组、集合和字典中存储的数据类型必须明确。不能插入类型不正确的数据，同时能够保证获取到相同类型的数据。

#### 数组
* 数组使用有序列表存储同一类型的多个值。
* 相同的值可以多次出现在一个数组的不同位置中。
* 存储到数组中的数据类型必须明确，方法是通过显式的类型标注或类型推断。
* 书写 Swift 数组的完整语法是`Array<SomeType>`，其中 SomeType 是数组中唯一允许存储的数据类型。

	``` Swift
	var shoppingList: Array<String> = Array<String>()
	```
* Swift 数组还有一种简单语法是`[SomeType]`，这种语法是 Swift 的推荐语法。

	``` Swift
	var foodList: [String] = [String]()
	```
* 构造数组的简单方法是使用字面量在`方括号[]`内，写入一个或多个数值，各数值之间由`逗号,`分割。

	``` Swift
	var fruitList: [String] = ["apple", "banana", "orange"]
	```
* 由于 Swift 的类型推断机制能够根据字面量判断数据类型，因此可以在构造数组时省略类型标注。

	``` Swift
	var fruitList = ["apple", "banana", "orange"]
	```
* 可以通过数组的方法、属性和下标语法来访问和修改数组。
* 可以使用数组的只读属性`count`来获取数组中的数据个数。

	``` Swift
	println("The fruit list contains \(fruitList.count) items.")
	```
* 可以通过判断`isEmpty`，来检查数组的`count`值是否为 0。

	``` Swift
	if fruitList.isEmpty {
		println("The fruit list is empty.")
	} else {
		println("The fruit list is not empty.")
	}
	```
* 可以使用`append`方法在数组后面添加新的数据项。

	``` Swift
	fruitList.append("watermelon")
	```
* 可以使用`加法赋值运算符 +=`在数组后面添加一个或多个相同类型的数据项。

	``` Swift
	fruitList += ["grape"]
	fruitList += ["peach", "pear"]
	```
* 可以直接使用下标语法来获取数组中的数据项，`arrayName[index]`。

	``` Swift
	var firstItem = fruitList[0]
	```
* Swift 中数组的下标索引值从 0 开始，而不是 1。
* 可以通过下标来改变某个已经存在的数据项的值。

	``` Swift
	fruitList[0] = "cherry"
	```
* 可以通过下标来一次改变一系列数据项的值，即使新数据和原有数据的数量是不一样的。

	``` Swift
	fruitList[0] = "cherry"
	```

* 当`count`的值为 0 时，最大索引值为 -1。
* 可以通过数组的`insert(atIndex:)`方法在某个具体索引值之前添加数据项。

	``` Swift
	fruitList.insert("lemon", atIndex: 0)
	```
* 可以通过数组的`removeAtIndex`方法来移除数组中的某一项，并返回被移除的数据项。

	``` Swift
	let removeItem = fruitList.removeAtIndex(0)
	```
* 可以通过数组的`removeLast`方法移除数组的最后一项。

	``` Swift
	let removeLastItem = fruitList.removeLast()
	```
* 可以通过使用 for-in 循环来遍历数组中所有的数据项。

	``` Swift
	for item in fruitList {
		println(item)
	}
	```
* 如果需要每个数据项的值和索引值，可以使用全局函数`enumerate`来进行数组遍历。enumerate 返回一个由数据项索引值和数据值组成的元组。

	``` Swift
	for (index, value) in enumerate(fruitList) {
		println("Item \(index + 1): \(value)")
	}
	```
* 使用构造方法能够创建一个由特定数据类型构成的空数组。

	``` Swift
	// 使用完整语法创建空数组
	var shoppingList: Array<String> = Array<String>()
	// 使用简单语法创建空数组（推荐语法）
	var foodList: [String] = [String]()
	```
* 如果代码上下文提供了类型信息，可以使用空数组语句将数组置空(空数组)，数组类型不变。

	``` Swift
	// 现在 foodList 数组内容有值了
	foodList.append("blueberry")
	// 使用空数组语句把 foodList 数组设置为空
	foodList = []
	```
* 通过把数据项数量(count)和适当类型的初始值(repeatedValue)传入数组构造函数，可以创建特定大小并且所有数据项都有指定默认值的数组。

	``` Swift
	// 创建了一个 Double 型数组，数组的数据项个数为 3,初始值是 0.0。
	var threeDoubles = [Double](count: 3, repeatedValue: 0.0)
	```
* 因为 Swift 拥有类型推断功能，所有构造具有特点大小和带默认值的数组时，不需要指定数组的数据类型。

	``` Swift
	// 创建了一个 Double 型数组，数组的数据项个数为 3,初始值是 2.5。
	var anotherThreeDoubles = Array(count: 3, repeatedValue: 2.5)
	```
* 可以通过使用加法操作符`+`，以及加法赋值操作符`+=`来组合两个已经存在的具有相同类型的数组。

	``` Swift
	// 创建了一个 Double 型数组，数组的数据项个数为 6,初始值是 [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]。
	var sixDoubles = threeDoubles + anotherThreeDoubles
	// 现在 fruitList 的值是之前 fruitList 的内容加上 foodList 的内容。
	fruitList += foodList
	```

#### 集合

#### 字典


#### 集合的可变性



-- End --
