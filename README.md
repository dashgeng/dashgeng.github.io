# 清风的博客

~~~个人博客~~~

URL: [dashgeng.github.io](http://www.dashgeng.com)

Email: [dashgeng@qq.com](dashgeng@qq.com)

# Swift Discovery
这是一个从 Swift 语言基础语法开始，发现与探索 Swift 语言的一段历程。

- [发现](#discovery)
- [探索](#探索)
- [开源协议](#开源协议)

# 要求
- Xcode 8.3+
- Swift 3.1

# Discovery 发现
## 清风注解 Swift
### 目录
- [x] Swift 初见
- [ ] 基础部分
- [ ] 基本运算符
- [ ] 字符串和字符
- [ ] 集合类型
- [ ] 控制流
- [ ] 函数
- [ ] 闭包
- [ ] 枚举
- [ ] 类和结构体
- [ ] 属性
- [ ] 方法
- [ ] 下标
- [ ] 继承
- [ ] 构造过程
- [ ] 析构过程
- [ ] 自动引用计数
- [ ] 可选链
- [ ] 错误处理
- [ ] 类型转换
- [ ] 嵌套类型
- [ ] 扩展
- [ ] 协议
- [ ] 泛型
- [ ] 访问控制
- [ ] 高级运算符

00.ASwiftTour
01.TheBasics
02.BasicOperators
03.StringsAndCharacters
04.CollectionTypes
05.ControlFlow
06.Functions
07.Closures
08.Enumerations
09.ClassesAndStructures
10.Properties
11.Methods
12.Subscripts
13.Inheritance
14.Initialization
15.Deinitialization
16.AutomaticReferenceCounting
17.OptionalChaining
18.ErrorHandling
19.TypeCasting
20.NestedTypes
21.Extensions
22.Protocols
23.Generics
24.AccessControl
25.AdvancedOperators

### 参考文献：

- [The Swift Programming Language](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/index.html
)

- [the-swift-programming-language-in-chinese](https://github.com/numbbbbb/the-swift-programming-language-in-chinese)

# 探索


# 开源协议
基于[MIT License](https://en.wikipedia.org/wiki/MIT_License)开源。



---

# Hyde

Hyde is a brazen two-column [Jekyll](http://jekyllrb.com) theme that pairs a prominent sidebar with uncomplicated content. It's based on [Poole](http://getpoole.com), the Jekyll butler.

![Hyde screenshot](https://f.cloud.github.com/assets/98681/1831228/42af6c6a-7384-11e3-98fb-e0b923ee0468.png)


## Contents

- [Usage](#usage)
- [Options](#options)
  - [Sidebar menu](#sidebar-menu)
  - [Sticky sidebar content](#sticky-sidebar-content)
  - [Themes](#themes)
  - [Reverse layout](#reverse-layout)
- [Development](#development)
- [Author](#author)
- [License](#license)
[测试](#测试)

## Usage

Hyde is a theme built on top of [Poole](https://github.com/poole/poole), which provides a fully furnished Jekyll setup—just download and start the Jekyll server. See [the Poole usage guidelines](https://github.com/poole/poole#usage) for how to install and use Jekyll.


## Options

Hyde includes some customizable options, typically applied via classes on the `<body>` element.


### Sidebar menu

Create a list of nav links in the sidebar by assigning each Jekyll page the correct layout in the page's [front-matter](http://jekyllrb.com/docs/frontmatter/).

```
---
layout: page
title: About
---
```

**Why require a specific layout?** Jekyll will return *all* pages, including the `atom.xml`, and with an alphabetical sort order. To ensure the first link is *Home*, we exclude the `index.html` page from this list by specifying the `page` layout.


### Sticky sidebar content

By default Hyde ships with a sidebar that affixes it's content to the bottom of the sidebar. You can optionally disable this by removing the `.sidebar-sticky` class from the sidebar's `.container`. Sidebar content will then normally flow from top to bottom.

```html
<!-- Default sidebar -->
<div class="sidebar">
  <div class="container sidebar-sticky">
    ...
  </div>
</div>

<!-- Modified sidebar -->
<div class="sidebar">
  <div class="container">
    ...
  </div>
</div>
```


### Themes

Hyde ships with eight optional themes based on the [base16 color scheme](https://github.com/chriskempson/base16). Apply a theme to change the color scheme (mostly applies to sidebar and links).

![Hyde in red](https://f.cloud.github.com/assets/98681/1831229/42b0b354-7384-11e3-8462-31b8df193fe5.png)

There are eight themes available at this time.

![Hyde theme classes](https://f.cloud.github.com/assets/98681/1817044/e5b0ec06-6f68-11e3-83d7-acd1942797a1.png)

To use a theme, add anyone of the available theme classes to the `<body>` element in the `default.html` layout, like so:

```html
<body class="theme-base-08">
  ...
</body>
```

To create your own theme, look to the Themes section of [included CSS file](https://github.com/poole/hyde/blob/master/public/css/hyde.css). Copy any existing theme (they're only a few lines of CSS), rename it, and change the provided colors.

### Reverse layout

![Hyde with reverse layout](https://f.cloud.github.com/assets/98681/1831230/42b0d3ac-7384-11e3-8d54-2065afd03f9e.png)

Hyde's page orientation can be reversed with a single class.

```html
<body class="layout-reverse">
  ...
</body>
```


## Development

Hyde has two branches, but only one is used for active development.

- `master` for development.  **All pull requests should be to submitted against `master`.**
- `gh-pages` for our hosted site, which includes our analytics tracking code. **Please avoid using this branch.**


## Author

**Mark Otto**
- <https://github.com/mdo>
- <https://twitter.com/mdo>


## License

Open sourced under the [MIT license](LICENSE.md).
