# 04_함수

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 선언 및 호출
- 반환값이 있는 경우
```swift
func 이름(매개변수1: 매개변수1타입) -> 반환타입 {
    return 반환값
}
```
```swift
func sum(a: Int, b: Int) -> Int {
    return a + b
}

sum(a: 1, b: 3)
```
<br>

- 반환값이 없는 경우
```swift
func 이름(매개변수1: 매개변수1타입) -> Void {
    return
}
func 이름(매개변수1: 매개변수1타입) {
    return
}
```
```swift
func printName(name: String) -> Void {
    print(name)
}
func printName(name: String) {
    print(name)
}

printName("SSangRRae")
```
<br>

- 매개변수가 없는 경우
```swift
func 이름() -> 반환값 {
    return 반환값
}
func 이름() {
    return
}
```
<br>

- 매개변수의 기본값이 있는 경우
```swift
func 이름(매개변수1: 매개변수1타입 = 기본값) -> 반환값 {
    return 반환값
}
```
```swift
func greeting(friend: String, me: String = "SSangRRae") {
    print("Hello \(friend) I'm \(me)")
}

// 매개변수의 값을 지정하지 않는 경우 기본값으로 지정됨
greeting(friend: "hana")
greeting(friend: "hana", me: "SR")
```
<br>

- 전달인자 레이블
```swift
func 이름(전달인자 매개변수1: 매개변수1타입) -> 반환값 {
    return 반환값
}
```
```swift
//함수 내부에서는 매개변수 이름을 사용
func greeting(to friend: String, from me: String) {
    print("Hello \(friend) I'm \(me)")
}

// 함수 호출시, 전달인자 레이블 사용
greeting(to: "hana", from: "SSangRRae")
```
<br>

- 가변 매개변수
```swift
// 가변 매개변수는 함수 당 1개만 가질 수 있음
func 이름(매개변수1: 매개변수1타입...) -> 반환값 {
    return 반환값
}
```
```swift
func greeting(me: String, friends: String...) -> String {
    return "Hello \(friend) I'm \(me)"
}

greeting(me: "SSangRRae", friends: "hana", "eric")
```
<br>

## 2. 데이터 타입으로서의 함수
```swift
func greeting(to friend: String, from me: String) {
    print("Hello \(friend) I'm \(me)")
}
func runAnother(function: (String, String) -> Void) {
    function("jenny", "mike")
}

var someFunction: (String, String) -> Void = greeting(to:from:)

someFunction("hana", "SSangRRae")
runAnother(greeting(to:from:))
```