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
* 可以使用数组的只读属性`count`来获取数组中的数据项个数。

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
* 当数据项的值必须是唯一的，或者	数据项的顺序并不重要时，我们使用集合当作数组的另一种形式来使用。
* Swift 中集合类型被写为`Set<someType`，这里的 SomeType 表示 Set 中允许存储的类型。集合没有类似数组的简化形式。
* 可以通过构造器语法创建一个特定类型的空集合。

	``` Swift
	var letters = Set<Character>()
	```
* 如果代码上下文提供了类型信息，可以使用空数组语句将集合置空(空集合)，集合类型不变。

	``` Swift
	// 现在 letters 集合内容有值了
	letters.append("a")
	// 使用空数组语句把 letters 集合设置为空
	letters = []
	```
* 使用数组字面量来构造集合，可以使用简化形式在方括号内写一个或多个值作为集合元素，各值之间用逗号隔开。

	``` Swift
	var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
	```
* 集合类型`Set`是不能从数组字面量中独立被推断出来的，因此集合类型必须显示声明。
* 由于 Swift 的类型推断功能，使用数组字面量构造集合时，无须为集合标注类型。

	``` Swift
	var favoriteGenres: Set = ["Rock", "Classical", "Hip hop"]
	```
* 可以通过集合的方法和属性来访问和修改集合。
* 可以使用集合的只读属性`count`来获取集合中的数据项个数。

	``` Swift
	println("I have \(favoriteGenres.count) favorite music genres.")
	```
* 可以通过判断`isEmpty`，来检查集合的`count`值是否为 0。

	``` Swift
	if favoriteGenres.isEmpty {
		println("As far as music goes, I'm not picky.")
	} else {
		println("I have particular music genres.")
	}
	```
* 可以通过集合的`insert(_:)`方法添加一个新元素。

	``` Swift
	favoriteGenres.insert("Jazz")
	```
* 可以通过集合的`remove(_:)`方法删除一个元素。如果传入的值是集合的一个元素，则删除该元素，并返回被删除的元素值；否则，如果集合不包含该值，返回 nil。

	``` Swift
	if let removedGenre = favoriteGenres.remove(“Rock”) {
		println("\(removedGenre)? I'm over it.")
	} else {
		println("I never much cared for that.")
	}
	```
* 可以通过`removeAll()`方法删除集合中所有元素。

	``` Swift
	favoriteGenres.removeAll()
	```
* 可以通过`contains(_:)`方法检查集合中是否包含一个特定的值。

	``` Swift
	if favoriteGenres.contains(“Funk”) {
		println("I get up on the good foot.")
	} else {
		println("It's too funky in here.")
	}
	```
* 可以通过 for-in 循环遍历集合中的所有值。

	``` Swift
	for genre in favoriteGenres {
		println("\(genre)")
	}
	```
* 可以通过`union(_:)`方法，根据两个集合的值创建一个新集合（并集）。
* 可以通过`subtract(_:)`方法，根据不在该集合中的值创建一个新集合（补集）。
* 可以通过`intersect(_:)`方法，根据两个集合中都包含的值创建一个新集合（交集）。
* 可以通过`exclusiveOr(_:)`方法，根据只属于其中一个集合，而不属于另一个集合的元素创建一个新的集合（对称差）。

	``` Swift
	let oddDigits: Set = [1, 3, 5, 7, 9]
	let evenDigits: Set = [0, 2, 4, 6, 8]
	let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]
	// oddDigits 和 evenDigits 并集的结果[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
	sorted(oddDigits.union(evenDigits))
	// oddDigits 和 evenDigits 交集的结果[]
	sorted(oddDigits.intersect(evenDigits))
	// oddDigits 和 singleDigitPrimeNumbers 补集的结果[1, 9]
	sorted(oddDigits.subtract(singleDigitPrimeNumbers))
	// oddDigits 和 singleDigitPrimeNumbers 对称差的结果[1, 2, 9]
	sorted(oddDigits.exclusiveOr(singleDigitPrimeNumbers))
	```
* 可以通过`相等运算符 ==`来判断两个集合是否包含相同的值。
* 可以通过`isSubsetOf(_:)`方法，来判断一个集合中的值，是否被包含在另一个集合中（子集）。
* 可以通过`isSuppersetOf(_:)`方法，来判断一个集合中包含的值，是否是另一个集合中所有的值（父集）。
* 可以通过`isStrictSubsetOf(_:)`方法或`isStrictSupersetOf(_:)`方法，来判断一个集合是否是另一个集合的子集合或父集合并且和特定集合不相等。（真子集 / 真父集）
* 可以通过`isDisjointWith(_:)`方法，来判断两个集合是否不含有相同的值。（互不相交）

	``` Swift
	let houseAnimals: Set = ["🐶", "🐱"]
	let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
	let cityAnimals: Set = ["🐦", "🐭"]
	// true，houseAnimals 是 farmAnimals 的子集
	houseAnimals.isSubsetOf(farmAnimals)
	// true，farmAnimals 是 houseAnimals 的父集
	farmAnimals.isSuperSetOf(houseAnimals)
	// true，farmAnimals 与 cityAnimals 互不相交
	farmAnimals.isDisjointWith(cityAnimals)
	```
* 存储在集合类型中的值必须是`可哈希化`的。也就是说集合中值的类型必须提供一个方法来计算它的哈希值。
* 哈希值是 Int 类型的，它和其它对象相同，用来比较相等与否。
 * 比如 a == b，它遵循的是 a.hashValue == b.hashValue。 
* Swift 的所有基本类型默认都是可哈希化的，它们可以作为集合的值或字典的键值类型。
* 没有关联值的枚举成员值默认也是可哈希化的。
* 集合的哈希值必须满足以下三种情况
 * a == a (自反性)
 * a == b 意味着 b == a (对称性)
 * a == b && b == c 意味着 a == c (传递性)

#### 字典


#### 集合的可变性



-- End --
