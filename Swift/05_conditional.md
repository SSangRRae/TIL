# 05_조건문

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. if-else
```swift
var num = 100

// 조건문에는 항상 Bool 타입이 들어와야 함
if num < 100 {
    print("100 미만")
} else if num > 100 {
    print("100 초과")
} else {
    print("100")
}
```

<br>

## 2. switch
```swift
var num = 100

// case마다 break를 해주지 않아도 break
switch num {
    case 0:
        print("0")
    case 1..<100:
        print("1~99")
    case 100:
        print("100")
    case 101...Int.max:
        print("over 100")
    // default 구문은 필수 사항
    default:
        print("Unknown")
}
```