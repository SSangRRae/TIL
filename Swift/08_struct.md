# 08_구조체

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 정의
```swift
struct Sample {
    // 가변 프로퍼티
    var mutableProperty: Int = 100
    // 불변 프로퍼티
    let immutableProperty: Int = 100
    // 타입 프로퍼티
    static var typeProperty: Int = 100
    // 인스턴스 메서드
    func instanceMethod() {
        print("instanceMethod")
    }
    // 타입 메서드
    static func typeMethod() {
        print("typeMethod")
    }
}
```

<br>

# 2. 사용
```swift
// 가변 인스턴스
var mutable: Sample = Sample()
// 구조체 내부 가변 프로퍼티 변경 가능
mutable.mutableProperty = 200

// 불변 인스턴스
let immutable: Sample = Sample()
// 불변 인스턴스이기 때문에 아무리 가변 프로퍼티라도 변경 불가능
// immutable.mutableProperty = 200

// 타입 프로퍼티 및 메서드
// 인스턴스에서 사용 불가능하고 구조체 타입 자체로 사용 가능
Sample.typeProperty = 300
Sample.typeMethod()
```