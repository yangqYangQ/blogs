---
title: 学习 Swift
date: 2021-01-11
tags:
  - Swift
categories:
  - 技术教程
  - Swift
updated: 2021-01-11 17:40:00
description: 
---
# Swift 语法

## 2.  MVVM 和 Swift 类型
Swift 中不同的类型包括：
`struct` 、`class` 、`functions` 、`generics 泛型` 、`protocol` 、`enum`

### 2.1 Generics
并不需要关心类型的类型

泛型的绝佳示例：`Array`

```swift
//声明 Array
//Element 是 类型参数（Type Parameter）
struct Array<Element> {
 . . .
 func append(_ element: Element) { . . . }
}

//使用 Array 时指定类型
var a = Array<Int>()
a.append(5)
a.append(22)
```

### 2.2 Functions

```swift
//function type
(Int, Int) -> Bool  
(Double) -> Void 
() -> Array<String>
() -> Void

var foo: (Double) -> Void 
func doSomething(what: () -> Bool) 
```

 ```swift
var operation: (Double) -> Double

func square(operand: Double) -> Double {
 return operand * operand
}

operation = square
//注意：不需要 operation(operand: 4)
let result1 = operation(4)  // results = 16

operation = sqrt  //sqrt 是 swift 内置的一个函数
let result2 = operation(4) // result2 = 2
 ```


# Swift 实战：Memorize Game With Swift

## 2. MVVM 和 Swift 类型

```swift
import SwiftUI

struct ContentView: View{
    var body: some View{
        HStack{
            ForEach(0..<4){ index in
                  CardView(isFaceUp: true)
            }
        }
            .padding()
            .foregroundColor(Color.orange)
        	.font(Font.largeTitle)
    }
}

struct CardView: View{
    var isFaceUp: Bool
    
    var body: some View{
        ZStack{
            if isFaceUp {
                RoundedRectangle(cornerRadius: 10.0).fill(Color.white)
                RoundedRectangle(cornerRadius: 10.0).stroke(lineWidth: 3)
                Text()
            } else {
                RoundedRectangle(cornerRadius: 10.0).fill()
            }
        }
    }
}
```



