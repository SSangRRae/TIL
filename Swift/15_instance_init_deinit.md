# 15_인스턴스의 생성과 소멸

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 이니셜 라이저
- 스위프트의 모든 인스턴스는 초기화와 동시에 유효한 값이 있어야함
- 프로퍼티에 미리 기본값을 할당하면, 인스턴스 생성과 동시에 초기값을 지니게 됨
```swift
class Person {
    var name: String
    var age: Int
    var nickName: String

    // 이니셜라이즈
    init(name: String, age: Int, nickName: String) {
        self.name = name
        self.age = age
        self.nickName = nickName
    }
}

let hana: Person = Person(name: "hana", age: 10, nickName: "하나")
let jenny: Person = Person(name: "jenny", age: 10)
```

<br>

- 자신의 init을 불러오기 위해 convenience 키워드 사용
```swift
class Person {
    var name: String
    var age: Int
    // 프로퍼티의 초기값이 필요 없을 경우 옵셔널
    var nickName: String?

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
     
    convenience init(name: String, age: Int, nickName: String) {
        self.init(name: name, age: age)
        self.nickName = nickName
    }
}
```


<br>

- 암시적 추출 옵셔널은 인스턴스 사용에 꼭 필요하지만, 초기값을 할당하지 않을 때 사용
```swift
class Puppy {
    var name: String
    var owner: Person!

    init(name: String) {
        self.name = name
    }
}

let happy: Puppy = Puppy(name: "happy")
happy.owner = jenny
```

<br>

- 실패 가능한 이니셜라이저
  - 이니셜라이저 매개변수로 전달되는 초기값이 잘못된 경우, 인스턴스 생성 실패후 nil 반환
  - 실패 가능한 이니셜라이저의 반환타입은 옵셔널 타입
```swift
class Person {
    var name: String
    var age: Int
    var nickName: String?

    init?(name: String, age: Int) {
        if (0...120).contains(age) == false {
            return nil
        }
        if name.characters.count == 0 {
            return nil
        }
        self.name = name
        self.age = age
    }
}

// 옵셔널 타입으로 선언해야 함
let john: Person? = Person(name: "john", age: 10)
```

<br>

## 2. 디이니셜라이저
- deinit은 클래스의 인스턴스가 메모리에서 해제되는 시점에 호출
- 인스턴스가 해제되는 시점에 해야하는 일을 구현 가능
- class 타입에서만 사용 가능
```swift
class Person {
    var name: String
    var pet: Puppy?

    init(name: String) {
        self.name = name
    }

    deinit {
        if let petName: pet?.name {
            print("deinit 입니다.")
        }
    }
}

let donald: Person = Person(name: "donald")
donald?.pet = happy

// donald 인스턴스가 더이상 필요 없기 때문에, 메모리에서 해제
donald = nil // deinit 입니다. 출력
```