# 10_열거형

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 정의
```swift
// 각 case는 그 자체가 고유의 값
enum Weekday {
    case mon
    case tue
    case wed
    case thu, fri, sat, sun
}

var day: Weekday = Weekday.mon
day = .tue
```

## 2. 원시값
- 정의
```swift
enum Fruit: Int {
    case apple = 0
    case grape = 1
    // 자동으로 1 증가
    case peach
}

print(Fruit.peach.rawValue) // 2

enum School: String {
    case elementary = "초등"
    case middle = "중등"
    case high = "고등"
    case university
}

print(School.university.rawValue) // university
```
<br>

- 원시값을 통한 초기화
```swift
// rawValue에 해당하는 case가 없을 수도 있으니
// optional type
let apple: Fruit? = Fruit(rawValue: 0)
```

<br>

## 3. 메서드
```swift
enum Month {
    case jan, feb, mar
    case apr, may, jun
    case jul, aug, sep
    case oct, nov, dec

    func printMessage() {
        switch self {
            case .jan, .feb, .mar:
                print("1, 2, 3")
            case .apr, .may, .jun:
                print("4, 5, 6")
            case .jul, .aug, .sep:
                print("7, 8, 9")
            case .oct, .nov, .dec:
                print("10, 11, 12")
        }
    }
}

Month.mar.printMessage()
```