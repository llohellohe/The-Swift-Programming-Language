# 枚举 (Enumerations)

枚举为一组相关值定义了一个通用的类型，使你能够在代码中使用这些值的同时保持类型安全。

|| 枚举为一组相关的值定义了一个通用的类型，让我们能够在代码中安全地操作这些值。

如果你熟悉C语言，你就知道C语言里的枚举是给相关名称赋予一系列整型值。相比C语言，Swift中的枚举更灵活，并且不需要为每一个枚举成员指定一个值。如果枚举成员被赋予了值（也就是“原始值”），这个值可以是字符串、字符、任一整型值或者浮点类型的值。

|| 如果对 C 语言比较熟悉，可能就会知道在 C 语言里枚举是给相关键值赋予一系列的整型值。但 Swift 的枚举更加灵活，而且不需要为每个枚举成员指定初始值。但如果枚举成员被赋予了初始值，这个值可以是字符、字符串、任何整型或浮点类型的值。

或者，枚举成员也可以成员值指定任一类型的关联值，就像其他语言的联合类型或者变体类型。你可以在一个枚举变量里定义一系列通用的相关成员，每一个成员都有一个相应类型的值与其关联。

|| 此外，就像其它编程语言中的联合类型或变体类型一样，Swift 的枚举变量可以给每个成员指定单独的值类型。我们可以把一系列相关的值定义为一个枚举变量，而且每个枚举成员都有相应的值与其关联。

枚举作为Swift语言中的“一等公民”，采用了许多一贯只被类支持的特性，比如计算属性，以提供关于枚举变量当前值的额外信息，以及实例方法，以提供关于枚举变量所代表值的功能。枚举类型也支持为枚举成员定义初始化值，还有在原有实现上扩展以增加其功能，以及遵循协议提供标准功能。

|| 枚举作为 Swift 的核心类型拥有强大的能力，它继承了很多一直以来只被类支持的特性，比如提供当前值之外更丰富信息的属性运算，或者用以展现该变量中所关联值的实例方法。枚举类型可以通过定义构造器为每个成员提供初始值，也可以在他们原始实现上扩展更多的功能，并通过遵循特定协议对外提供标准功能。


关于这些特性的更多信息，请参考属性，方法，初始化，扩展，以及协议。

|| 关于这些特性的更多信息，请参考[属性]()，[方法]()，[初始化]()，[扩展]()，以及[协议]()。


## 枚举语法

## ||  枚举类型的语法

你可以用enum关键字引入枚举类型，并把完整的定义用一对大括号包裹起来：

|| 我们可以用 `enum` 关键字定义枚举变量，并把完整的定义用一对大括号包裹起来：

```
enum SomeEnumeration {
    // 枚举定义
}
```

以指南针的四个方位为例：

|| 以指南针的四个方位为例：

```
enum CompassPoint {
    case North
    case South
    case East
    case West
} 
```

在枚举变量内定义的值（例如North、South、East、West）称为这一枚举变量的成员值或者成员。Case 关键字表明将被定义的新的一行成员值。

|| 这些被枚举变量定义的值（如 North、South、East、West）被称作该枚举变量的成员。`case` 关键字表示这一行定义了新的成员值。

> 注意：不像C和Objective－C，Swift语言中的枚举类型在创建时并不会被赋予一个默认的整型值。在上面的CompassPoints例子中，North、South、East、West并不是默认为0，1，2，3。相反，这些不同的枚举成员都是完备的值，并且以显式声明的CompassPoint作为其类型。

> 注意：不像 C 或者 Objective-C，Swift 中的枚举类型不会在创建时被赋予一组初始的整型值。在上面的 `CompassPoint` 指南针例子中，`North`、`South`、`East`、`West` 并不是默认的 `0`，`1`，`2`，`3`。相反地，通过 `CompassPoint` 类型的显示声明，这些枚举成员会拥有各自独立的类型。

多个成员值可以用逗号分隔在同一行出现：

|| 多个成员值可以写在同一行，使用逗号分隔：

```
enum Planet {
    case Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
}
```

每一个枚举变量都定义了一个全新的类型。和Swift中的其他类型一样，枚举变量的命名（比如CompassPoint和Planet）都需要以大写字母开头，并采用单数而不是复数形式，这样阅读时就一目了然了。

|| 每个枚举变量都定义了一个全新的类型。和 Swift 中其它类型一样，枚举变量的命名（比如`CompassPoint` 和 `Planet`）都需要以大写字母开头，并采用单数而不是复数形式，这样阅读时就一目了然。

```
var directionToHead = CompassPoint.West
```

当以CompassPoint其中一个值初始化时， 编译器将推断directionToHead的类型。而一旦把directionToHead以CompassPoint类型完成声明后，在设置它为CompassPoint其他值的时候，你就可以使用更为简短便捷的点语法了：

|| 当以 `CompassPoint` 其中一个值初始化时，编译器将推断 `directionToHead` 的类型。而一旦把 `directionToHead` 以 `CompassPoint` 类型声明后，就可以用很简单的方法设置它为 `CompassPoint` 的其它值：

```
directionToHead = .East
```

directionToHead的类型已知了，因此你可以在赋值时省略类型。当遇到显式声明的枚举变量时，借助点语法可以使你的代码更具可读性。

|| 一旦 `directionToHead` 的类型已知，我们就可以在赋值时忽略类型的指定。当遇到显式声明的枚举变量时，这种语法可以让代码更具可读性。


## 用Switch语句匹配枚举值

你可以通过Switch语句匹配某一枚举值：

|| 我们可以通过 `Switch` 语句匹配某个枚举值：

```
directionToHead = .South
switch directionToHead {
case .North:
    println("Lots of planets have a north")
case .South:
    println("Watch out for penguins")
case .East:
    println("Where the sun rises")
case .West:
    println("Where the skies are blue")
}
// 输出 "Watch out for penguins"
```

这段代码可以这样理解：

|| 这段代码可以这样理解：

“考虑directionToHead的值：当它等于.North时，打印 “Lots of planets have a north” ；当它等于.South时，打印  “Watch out for penguins” ”，后续省略。

|| “对比 `directionToHead` 的值：如果它等于 `.North`，输出 "Lots of planets have a north"；如果它等于 `.South`，正如此例，将输出 "Watch out for penguins"。”

|| 以此类推。

就像在流程控制里所描述的那样，switch语句在确定枚举变量的值的时候要全面完备。如果删掉.West对应的情况，这段代码将不能通过编译，因为它没有考虑到完整的CompassPoint 成员列表。要求全面完备确保了枚举变量不会被意外忽略。

|| 就像在 [流程控制]() 里描述的一样，`switch` 语句必须考虑到所有的枚举成员。在上面的例子中，如果 `case` 语句忽略了 `.West` 成员，代码编译将不会通过，因为它没照顾到所有 `CompassPoint` 的成员。这种严格的要求确保了每个枚举成员不会被意外地忽略。

当不能为每一个枚举变量都提供case关键字时，可以为 那些没有一一提到的枚举成员设置一个default关键字：

|| 当不能为每一个枚举成员都提供 `case` 语句时，可以给那些没有显式提到的成员设置一个 `default` 关键字：

```
let somePlanet = Planet.Earth
switch somePlanet {
case .Earth:
    println("Mostly harmless")
default:
    println("Not a safe place for humans")
}
// 输出 "Mostly harmless"
```


## 相关值

## || 相关值

上一节内容的例子展示了枚举成员是具有独立定义和独立类型的值。你可以为Planet.Earth设置一个常量或变量，以及后续做检验。但有时为枚举成员关联其他类型的值将会很有用。这让你能为枚举成员添加额外的配置信息，并允许其在每次使用时改变其信息内容。

|| 上一节的例子展示了枚举成员是具有独立定义和独立类型的值。我们可以为 `Planet.Earth` 赋值为常量或变量，或者后面再调整。有时在每个枚举成员旁边关联值的类型会很有用，因为这可以让我们在声明枚举成员时附带更多额外的信息，而且允许我们在以后的每次使用过程中修改这些信息。

你能为Swift中的枚举变量定义任意给定类型的关联值，并且如果需要，这些关联值的类型可以根据枚举成员而不同。这样的枚举变量在其他编程语言中被称为可区分联合类型、带标签的联合类型或者变异类型。

|| Swift 中的枚举类型可以存储任何指定类型的相关值，而且如果需要的话，每个枚举成员的类型都可以互不一样。这种枚举类型就像是在其它编程语言中被大众熟知的*鉴别联集*、*标签联合*或*变体类型*。

例如，假设一个存货清单跟踪系统需要跟踪两种带有不同条形码的产品。一种产品被打上UPC－A格式的一维条形码，这一格式使用0到9的数字。每个条形码包含一个“号码系统”数字，紧跟着十个“标识符”数字，最后还有一个“校验位”数字以验证该条形码是否被正确扫描了。

|| 举个例子，在一个存货清单跟踪系统中需要跟踪两种带有不同条形码的产品。其中一些产品使用由数值 0 到 9 表示的一维条形码 UPC-A。这种条形码一开始会有一个指定进制的数值，然后紧跟 10 位标识符，最后会有一个校验位用来检查该条形码是否被正确地扫描。

![](http://gtms04.alicdn.com/tps/i4/TB1y.hbFFXXXXXibFXX.wCCNpXX-366-175.png)

另一种产品被打上QR格式的二维码，这一格式使用ISO 8859-1的任意字符，并且可以编码长达2953个字符的字符串。

|| 而另一些产品则使用了 QR 格式的二维码，这一格式允许使用 ISO 8859-1 字符集的任意字符，并且可以表示长达 2953 个字符的字符串。

![](http://gtms01.alicdn.com/tps/i1/TB11AE1FFXXXXaSXXXX39VBMpXX-257-257.png)

如果我们的存货清单跟踪系统能分别以长度为三的整型数组的形式保存UPC－A格式，并以任意长度的字符串格式保存QR格式就好了。

|| 如果我们的存货清单跟踪系统能同时以三个整型数组的形式储存 UPC－A 格式，并以任意长度的字符串格式保存QR格式的话，那就很方便了。

```
enum Barcode {
    case UPCA(Int, Int, Int)
    case QRCode(String)
}
```

在 Swift 中，可以这样定义这两种产品条纹码的枚举变量：

|| 在 Swift 中，可以这样声明兼容两种产品条形码的枚举类型：

```
enum Barcode {
    case UPCA(Int, Int, Int)
    case QRCode(String)
}
```

这段代码可以这样理解：

|| 这段代码可以这样理解：

“定义一个叫Barcode的枚举类型，可包含关联长度为三的整型数组的UPCA 以及关联字符串的QRCode”。

|| “声明一个叫 `Barcode` 的枚举类型，它包含了以三个整型数组（`Int`,`Int`,`Int`）的形式储存的 UPC，以及以字符串（`String`）形式存储的 `QRCode` ”。

这一定义不包含任何确切整型值或者字符串，它只定义Barcode.UPCA和Barcode.QRCode对应Barcode枚举变量和常量可以存储的关联值的类型。

|| 这个声明不包含任何确切的整型值或者字符串，它只是在 `Barcode.UPCA` 和 `Barcode.QRCode` 的描述中定义了 `Barcode` 的枚举变量或常量允许使用的值类型。

现在条纹码可以使用任一类型创建：

|| 现在条形码可以通过任意一个类型创建：

```
var productBarcode = Barcode.UPCA(8, 85909_51226, 3)
```

这个例子创建了一个叫productBarcode的新变量，赋予它一个关联了(8, 8590951226, 3)数组的Barcode.UPCA。上面的“标识符”值中包含了一个下划线：85909_51226，让它作为条纹码更具可读性。


|| 这个例子创建了一个叫 `productBarcode` 的新变量，并赋予了它由三个数值数组关联的 `Barcode.UPCA` 成员值。在上面的 10 位标识符中出现了一个下划线 `85909_51226`，这是为了让它作为条形码更具可读性。

我们也可以赋予这个产品另外一个条纹码：

|| 或者，这个产品我们可以赋予它另外一种条形码：


```
productBarcode = .QRCode("ABCDEFGHIJKLMNOP")
```

这时，原有的Barcode.UPCA和它的整型值被替换成新的Barcode.QRCode和字符串。类型为Barcode的常量和变量可以保存.UPCA或者.QRCode（以及它们的关联值），并且在任一给定时间内只能保存其中一个。

|| 这时原有的 `Barcode.UPCA` 和它关联的数值会被替换成新的 `Barcode.QRCode` 字符串。已经被定义为 `Barcode` 类型的变量或常量允许使用 `.UPCA` 或者 `.QRCode` 类型存储数据，但同一时刻只能使用其中一种类型。

和之前一样，我们可以使用switch语句来检验不同类型的条纹码。然而这次，可以把关联值抽取出来作为switch语句的一部分。你可以抽取关联值作为一个常量（带有前缀let）或者变量（带有前缀var）以在switch语句的case主体内使用：

|| 和前面的一样，使用 `switch` 语句可以用来检查不同类型的条形码，但这次，我们可以把关联值抽取出来作为 `switch` 语句的一部分。我们可以把关联值以常量（使用前缀 `let`）或者变量（使用前缀 `var`）抽出，放在 `case` 内容里面。

```
switch productBarcode {
case .UPCA(let numberSystem, let identifier, let check):
    println("UPC-A with value of \(numberSystem), \(identifier), \(check).")
case .QRCode(let productCode):
    println("QR code with value of \(productCode).")
}
// 输出 "QR code with value of ABCDEFGHIJKLMNOP."
```

如果一个枚举成员所有的都能被抽取为常量，或者都能被抽取为变量，你可以在枚举成员名称前放一个let或者var作为注解，简单来说就是这样：

|| 如果一个枚举成员所有的关联类型都能被抽取为常量变量，则可以在枚举成员名称前放一个 `let` 或者`var` 声明，简单来说就是这样：

```
switch productBarcode {
case let .UPCA(numberSystem, identifier, check):
    println("UPC-A with value of \(numberSystem), \(identifier), \(check).")
case let .QRCode(productCode):
    println("QR code with value of \(productCode).")
}
// 输出 "QR code with value of ABCDEFGHIJKLMNOP."
```


## 原始值

## || 原始值

上面关联值小节里的条纹码的例子展示了枚举成员是如何声明其和不同类型的值相关联。作为关联值的替代，枚举成员也可以在初始化时预先设置默认值（也叫原始值），并且其类型保持相同。

|| 在上面 [关联值]() 的例子中，描述了如何为每个枚举成员声明不同的存储类型。另外，所有枚举成员可以使用同一种类型预定义指定的值（一般称作 *原始值*）。

以下是一个例子展示命名的枚举成员和原始的ASCII码相关联：

|| 下面的例子展示的是在每个枚举成员旁边定义了 ASCII 原始值:

```
 enum ASCIIControlCharacter: Character {
    case Tab = "\t"
    case LineFeed = "\n"
    case CarriageReturn = "\r"
}
```

这里，一个名为ASCIIControlCharacter的枚举类型的原始值被定义为字符类型，并且被设置为一些更为常见的ASCII控制字符。关于字符可参考“字符串与字符”一章。

|| 在这个例子里，一个名为 `ASCIIControlCharacter` 的枚举类型的值被定义为 `Character`，并给每个枚举成员预设了一些常见的 ASCII 字符。关于字符可参考 [字符串与字符]() 一章。

注意原始值和关联值并不一样。像这个例子中的三个ASCII码一样，原始值是你在代码中第一次定义枚举类型时就已设置的值，并且一个特定枚举成员的原始值始终不会改变。而关联值是你根据某一枚举成员创建一个常量或变量时才设置的值，并且每次创建时都可以不同。

|| 注意原始值和关联值并不一样，就像这个例子中的三个 ASCII 码。原始值是在代码中第一次定义枚举类型时就已设置的值，并且一个特定枚举成员的原始值始终不会改变。而关联值是根据某一枚举成员创建一个常量或变量时才设置的值，并且每次创建时都可以不同。

原始值可以是字符串、字符，或者任一整型和浮点数类型。每个原始值在其枚举类型声明时都必须保持唯一。当整型被用作原始值时，如果一些枚举成员没有设置特定值，它们的原始值会自增。

|| 原始值可以是字符串、字符，或者任一整型和浮点数类型。每个原始值在其枚举类型声明时都必须保持唯一。当整型被用作原始值时，如果一些枚举成员没有设置特定值，它们的原始值会自增。

下面的枚举类型是对之前Planet枚举类型的一个改良，使用整型的原始值代表每个星球离太阳距离大小的顺序。

|| 下面的枚举类型是对之前 `Planet` 枚举类型的一个改良，使用整型的原始值代表每个星球距离太阳近远的顺序。

```
enum Planet: Int {
    case Mercury = 1, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
}
```

这里的自增意味着Planet.Venus的原始值为2，依此类推。

|| 这里的自增意味着 `Planet.Venus` 的原始值为 2，依此类推。

你可以通过枚举成员的toRaw方法访问其原始值：

|| 我们可以通过枚举成员的 `toRaw` 方法访问其原始值：

```
let earthsOrder = Planet.Earth.toRaw()
// earthsOrder 为 3
```

你也可以通过枚举类型的fromRaw方法去试图查找带有某一特定原始值的枚举成员。这个例子通过其原始值为7找到了Uranus：

|| 也可以通过枚举类型的 `fromRaw` 方法去试图检索带有某一特定原始值的枚举成员。这个例子通过原始值为 7 找到了 `Uranus`：

```
let possiblePlanet = Planet.fromRaw(7)
// possiblePlanet类型为Planet?并且值等于Planet.Uranus
```

然而，不是所有的int值都能匹配到一个星球。因此，fromRaw方法返回一个可选的枚举成员。以上的例子中，possiblePlanet的类型是”Planet?”或者”可选Planet”。

|| 不过不是所有的 `Int` 值都会匹配到一个星球。所以，`fromRaw` 方法返回的是一个 *可选的* 枚举成员。上面的例子中，`possiblePlanet` 的类型是 `Planet?` 或者 ”可选 `Planet`”

如果你试图查找位置为9的星球，fromRaw方法返回的这个可选Planet将为nil：

|| 如果试图检索位置为 9 的星球，`fromRaw` 方法返回的这个可选 `Planet` 将为 `nil`：

```
let positionToFind = 9
if let somePlanet = Planet.fromRaw(positionToFind) {
    switch somePlanet {
    case .Earth:
        println("Mostly harmless")
    default:
        println("Not a safe place for humans")
    }
} else {
    println("There isn't a planet at position \(positionToFind)")
}
// 输出 "There isn't a planet at position 9"
```

这个例子使用可选绑定试图访问原始值为9的星球。如果可以取回，if let somePlanet = Planet.fromRaw(9)这一语句将取回一个可选Planet并把它赋予somePlanet。而这种情况下是不可能取回一个位置为9的星球，因此，else分支就被执行了。 


|| 这个例子使用可选绑定试图访问原始值为 9 的星球。如果可以访问，则 `if let somePlanet = Planet.fromRaw(9)` 这一语句将一个可选 `Planet` 赋值给 `somePlanet`。但目前没有办法找到一个位置为 9 的星球，所以 `else` 分支就被执行了。 






































