# 14_상속

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 스위프트의 상속은 클래스, 프로토콜 등에서 사용
- 열거형, 구조체는 상속 불가능
- 다중상속을 지원하지 않음
- `final` 키워드로 상속 방지

<br>

## 2. 상속과 재정의
```swift
class 이름: 상속받을 클래스 이름 {
    // 구현부
}
```
```swift
class Person {
    var name: String = ""

    func selfIntroduce() {
        print("저는 \(name)입니다.")
    }

    final func sayHello() {
        print("안농~~~~")
    }

    // 재정의 불가 메서드 - static
    // `static` == `final class`
    static func typeMethod() {
        print("type Method - static")
    }

    // 재정의 가능 메서드 - class
    class func classMethod() {
        print("type Method - class")
    }
}

class Student: Person {
    var major: String = ""

    // override 키워드로 부모 메서드 덮어 쓰기
    override func selfIntroduce() {
        print("저는 \(name)이고 전공은 \(major)입니다.")
    }

    override class func classMethod() {
        print("overriden type method - class")
    }
}
```