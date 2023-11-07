# 20_익스텐션

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 구조체, 클래스, 열거형, 프로토콜 타입에 새로운 기능을 추가할 수 있는 기능
- 기능을 추가하려는 타입의 구현된 소스 코드를 알지 못하거나 볼 수 없다 해도, 타입만 알고 있다면 그 타입의 기능을 확장할 수 있음
- 익스텐션으로 추가할 수 있는 기능
   - 연산 타입 프로퍼티
   - 연산 인스턴스 프로퍼티
   - 타입 메서드
   - 인스턴스 메서드
   - 이니셜라이저
   - 서브스크립트
   - 중첩 타입
- 기존에 존재하는 기능을 재정의할 수는 없음
```swift
extension Int {
    var isEven: Bool {
        return self % 2 == 0
    }

    var isOdd: Bool {
        return self % 2 == 1
    }

    func multiply(by n: Int) -> Int {
        return self * n
    }
}
extension String {
    init(intTypeNumber: Int) {
        self = "\(intTypeNumber)"
    }
    init(doubleTypeNumber: Double) {
        self = "\(doubleTypeNumber)"
    }
}

print(1.isEven) // false
print(1.isOdd) // true
print(3.multiply(by: 2)) // 6

let stringFromInt: String = String(intTypeNumber: 100)
let stringFromDouble: String = String(doubleTypeNumber: 100.0)
```
