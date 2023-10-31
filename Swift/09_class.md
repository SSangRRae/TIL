# 09_클래스

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 정의
```swift
class Sample {
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
    // 1. 재정의 불가 타입 메서드
    static func typeMethod() {
        print("typeMethod: static")
    }
    // 2. 재정의 가능 타입 메서드
    class func classMethod() {
        print("typeMethod: class")
    }
}
```

<br>

## 2. 사용
```swift
var mutableReference: Sample = Sample()
let immutableReference: Sample = Sample()

// 구조체와 다르게 가변, 불변 인스턴스에서 가변 프로퍼티 값 변경 가능
mutableReference.mutableProperty = 200
immutableReference.mutableProperty = 200

Sample.typeProperty = 200
Sample.typeMethod()
```