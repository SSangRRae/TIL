# 19_프로토콜

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 특정 역할을 수행하기 위한 메서드, 프로퍼티, 이니셜라이저 등의 요구사항을 정의
- 구조체, 클래스, 열거형은 프로토콜을 채택해서, 프로토콜의 요구사항을 실제로 구현
- 어떤 프로토콜의 요구사항을 모두 따르는 타입은 그 프로토콜을 준수한다고 표현
- 프로토콜의 요구사항을 충족시키려면 프로토콜이 제시하는 기능을 모두 구현
```swift
protocol Talkable {
    // 프로퍼티 요구
    /*
    - 프로퍼티 요구는 항상 var 키워드를 사용
    - get은 읽기만 가능해도 상관 없다는 뜻
    - get과 set을 모두 명시하면 읽기 쓰기 모두 가능한 프로퍼티여야 함
    */
    var topic: String { get set }
    var language: String { get }

    // 메서드 요구
    func talk()
    // 이니셜라이저 요구
    init(topic: String, language: String)
}
```

<br>

## 2. 프로토콜 채택 및 준수
```swift
// Person 구조체는 Talkable 프로토콜을 채택
struct Person: Talkable {
    var topic: String
    let language: String

    func talk() {
        print("\(topic)에 대하여 \(language)로 대화")
    }

    init(topic: String, language: String) {
        self.topic = topic
        self.language = language
    }
}
```

<br>

## 3. 상속
- 프로토콜은 클래스와 달리 다중상속 가능
```swift
protocol Readable {
    func read()
}

protocol Writeable {
    func write()
}

protocol ReadWriteSpeakable: Readable, Writebale {
    func speak()
}

struct SomeType: ReadWriteSpeakalbe {
    func read() {
        print("read")
    }
    func write() {
        print("write")
    }
    func speak() {
        print("speak")
    }
}
```

<br>

## 4. 클래스 상속과 프로토콜
- 클래스에서 상속과 프로토콜 채택을 하려면 클래스, 프로토콜 순으로 작성
```swift
class SuperClass: Readable {
    func read() { print("read") }
}
class SubClass: SuperClass, Writeable {
    func write() { print("write") }
}
```

<br>

## 5. 준수 확인
- 인스턴스가 특정 프로토콜을 준수하는지 확인
- `is`, `as` 연산자 사용
```swift
let sup: SuperClass = SuperClass()
let sub: SubClass = SubClass()

var someAny: Any = sup
someAny is Readable // true
someAny is Writeable // false

someAny = sub
someAny is Readable // true
someAny is Writeable // true
```
```swift
var someAny: Any = sup

if let someReadable: Readable = someAny as? Readable {
    someReadalbe.read()
}
```