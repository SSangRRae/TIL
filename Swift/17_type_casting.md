# 17_타입 캐스팅

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 인스턴스의 타입을 확인하는 용도
- 클래스의 인스턴스를 부모 혹은 자식 클래스의 타입으로 사용할 수 있는지 확인하는 용도
```swift
class Person {
    var name: String = ""
    func breath() {
        print("숨을 쉽니다")
    }
}

class Student {
    var school: String = ""
    func goToSchool() {
        print("등교 합니다")
    }
}

class UniversityStudent {
    var major: String = ""
    func goToMT() {
        print("멤버쉽 트레이닝 갑니다")
    }
}

var yagom: Person = Person()
var hana: Student = Student()
var jason: UniversityStudent = UniversityStudent()
```

<br>

- `is` : 타입 확인 
```swift
var result: Bool

result = yagom is Person // true
result = yagom is Student // false
result = yagom is UniversityStudent // false

result = hana is Person // true
result = hana is Student // true
result = hana is UniversityStudent // false

result = jason is Person // true
result = jason is Student // true
result = jason is UniversityStudent // true
```

<br>

- `as` : 업캐스팅
   - 부모클래스의 인스턴스로 사용할 수 있도록 컴파일러에게 타입정보를 전환
   - `Any` 혹은 `AnyObject`로도 타입정보를 변환할 수 있음 (생략가능)
```swift
var mike: Person = UniversityStudent as Person
var jenny: Student = Student()
var jina: Any = Student() // as Any 생략가능
```

<br>

- 다운캐스팅
   - 자식 클래스의 인스턴스로 사용할 수 있도록 컴파일러에게 인스턴스의 타입정보를 전환
   - `as?` : 조건부 다운 캐스팅
   - `as!` : 강제 다운 캐스팅
```swift
var optionalCasted: Student?

optionalCasted = mike as? UniversityStudent
optionalCasted = jenny as? UniversityStudent // nil
optionalCasted = jina as? UniversityStudent // nil
optionalCasted = jina as? Student // nil
```
```swift
var forcedCasted: Student

forcedCasted = mike as! UniversityStudent
// 아래 3줄은 런타임 오류
// forcedCasted = jenny as! UniversityStudent
// forcedCasted = jina as! UniversityStudent
// forcedCasted = jina as! UniversityStudent
```