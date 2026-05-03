[上一级](./007-Swift-study.md)



# Memorize Game With Swift

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



