# 18_assert와 guard

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 애플리케이션이 동작 도중에 생성하는 다양한 결과값을 동적으로 확인하고 안전하게 처리할 수 있도록 확인하고 빠르게 처리 가능

<br>

## 2. assert
- `assert(_:_:file:line:)` 함수 사용
- assert 함수는 디버깅 모드에서만 동작
- 배포하는 애플리케이션에서 제외됨
- 주로 디버깅 중 조건의 검증을 위해 사용
```swift
var someInt: Int = 0

// someInt가 0이면, assert 함수 통과
// 아니면, 'someInt != 0' 출력 후, 동작 중지
// 메세지는 생략 가능
assert(someInt == 0, "someInt != 0")
```
```swift
func functionWithAssert(age: Int?) {
    assert(age != nil, "age == nil")
    assert((age! >= 0) && (age! <= 130), "나이값 입력이 잘못되었습니다.")
    print("당신의 나이는 \(age!)세 입니다.")
}

functionWithAssert(age: 50)
functionWithAssert(age: -1) // 동작 중지
functionWithAssert(age: nil) // 동작 중지
```

<br>

## 3. guard
- 잘못된 값의 전달 시, 특정 실행구문을 빠르게 종료
- 디버깅 모드 뿐만 아니라 어떤 조건문에서도 동작
- guard의 else 블럭 내부에는 특정 코드블럭을 종료하는 지시어가 있어야함 (return, break)
- 타입 캐스팅, 옵셔널과도 자주 사용됨
- 그 외 단순 조건 판단 후, 빠르게 종료할 때도 용이
```swift
func functionWithGuard(age: Int?) {
    guard let unwrappedAge = age,
        unwrappedAge < 130,
        unwrappedAge >= 0 else {
            print("나이값 입력이 잘못되었습니다")
            return
        }
    print("당신의 나이는 \(unwrappedAge)입니다.")
}
```
```swift
func someFunction(info: [String: Any]) {
    guard let name = info["name"] as? String else {
        return
    }
    guard let age = info["age"] as? Int, age >= 0 else {
        return
    }

    print("\(name) : \(age)")
}
```