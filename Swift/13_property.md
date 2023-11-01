# 13_프로퍼티

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 정의
- 프로퍼티는 구조체, 클래스, 열거형 내부에 구현
- 다만, 열거형 내부에는 연산 프로퍼티만 구현
- 연산 프로퍼티는 `var` 로만 선언

<br>

## 2. 종류
- 저장 프로퍼티
- 연산 프로퍼티 : 지역/전역 변수에 사용 가능
- 인스턴스 프로퍼티
- 타입 프로퍼티
```swift
struct Student {

    // 인스턴스 저장 프로퍼티
    var name: String = ""
    var `class`: String = "Swift"
    var korAge: Int = 0

    // 인스턴스 연산 프로퍼티
    var westernAge: Int {
        get {
            return korAge - 1
        }
        set(inputValue) {
            korAge = inputValue + 1
        }
    }

    // 타입 저장 프로퍼티
    static var typeDescription: String = "학생"

    // 인스턴스 메서드
    /*
    func selfIntroduce() {
        print("저는 \(self.class)반 \(name)입니다.")
    }
    */

    // 읽기 전용 인스턴스 연산 프로퍼티
    // 쓰기 전용은 없음
    // 위 selfIntroduce 메서드를 변환
    var selfIntroduction: String {
        get {
            return "저는 \(self.class)반 \(name)입니다."
        }
    }
}

print(Student.selfIntroduction)

var me: Student = Student()
me.korAge = 10
print(me.westernAge) // 9
```

<br>

## 3. 프로퍼티 감시자
- 프로퍼티 감시자를 사용하면, 프로퍼티 값이 변경될 때 원하는 동작을 수행할 수 있음
- 연산 프로퍼티 내의 프로퍼티 감시자 사용 불가
```swift
struct Money {
    var currencyRate: Double = 1100 {
        // newRate 생략 가능 -> newValue
        willSet(newRate) {
            print("환율이 \(currencyRate)에서 \(newRate)로 변경될 예정")
        }
        // oldRate 생략 가능 -> oldValue
        didSet(oldRate) {
            print("환율이 \(oldRate)에서 \(currencyRate)로 변경됨")
        }
    }
}
```

<br>

- 지역/전역 변수에도 사용 가능
```swift
var a: Int = 100 {
    willSet {
        print("\(a)에서 \(newValue)로 변경 예정")
    }
    didSet {
        print("\(oldValue)에서 \(a)로 변경")
    }
}
```