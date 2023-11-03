# 16_옵셔널 체이닝

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 옵셔널 요소 내부의 프로퍼티로 또다시 옵셔널이 연속적으로 연결된 경우 유용하게 사용 가능
```swift
class Person {
    var name: String
    var job: String
    var home: Apartment?

    init(name: String) {
        self.name = name
    }
}

class Apartment {
    var buildingNumber: String
    var roomNumber: String
    var `guard`: Person?
    var owner: Person?

    init(dong: String, ho: String) {
        buildingNumber = dong
        roomNumber = ho
    }
}


// 옵셔널 체이닝을 사용하지 않는 경우
func guardJob(owner: Person?) {
    if let owner = owner {
        if let home = owner.home {
            if let `guard` = home.guard {
                if let guardJob = `guard`.job {
                    print("직업은 \(guardJob)")
                }
                else {
                    print("직업은 없습니다.")
                }
            }
        }
    }
}

// 옵셔널 체이닝을 사용한 경우
func guardJob(owner: Person?) {
    if let guardJob = owner?.home?.guard?.job {
        print("직업은 \(guardJob)")
    }
    else {
        print("직업은 없습니다.")
    }
}

let yagom: Person? = Person(name: "yagom")
let apart: Apartment? = Apartment(dong: "101", ho: "202")
let superman: Person? = Person(name: "superman")

guardJob(owner: yagom) // 직업은 없습니다.

yagom?.home = apart
yagom?.home?.guard = superman
yagom?.home?.guard?.job = "경비원"

guardJob(owner: yagom) // 직업은 경비원
```

<br>

## 2. nil 병합 연산자
- var sample: String = A ?? B
- A가 nil이면 B를 sample에 넣는다는 뜻
```swift
var guardJob: String

guardJob = yagom?.home?.guard?.job ?? "슈퍼맨"
print(guardJob) // 경비원

yagom?.home?.guard?.job = nil
guardJob = yagom?.home?.guard?.job ?? "슈퍼맨"
print(guardJob) // 슈퍼맨
```