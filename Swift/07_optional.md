# 07_옵셔널

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 옵셔널
- 값이 있을 수도, 없을 수도 있음
- nil의 가능성을 명시적으로 표현
- 전달받은 값이 옵셔널이 아니라면, nil체크를 하지 않고 사용 가능
```swift
// 컴파일 오류 발생
let num: Int = nil

let num: Int? = nil
```
```swift
func someFunc(someParm: Int?) {

}
someFunc(someParm: nil)
```

<br>

## 2. 값 추출
- 옵셔널 바인딩: nil 체크 + 안전한 값 추출 가능
```swift
func printName(name: String) {
    print(name)
}
var myName: String! = nil

// if-let 방식
if let name: String = myname {
    printName(name)
} else {
    print("myName == nil")
}
```

<br>

- 강제 추출 (Force Umwrapping): 많이 추천하지 않는 방식
```swift
func printName(name: String) {
    print(name)
}

var myName: String? = "SSangRRae"

printName(myName!)

myName = nil

// 강제 추출 시, 값이 없으므로 런타임 오류 발생
print(myName!)

var yourName: String! = nil

// nil 값이 전달되기 때문에 런타임 오류 발생
printName(yourName)
```