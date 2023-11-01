# 12_클로저

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 정의
```swift
{(매개변수 목록) -> 반환타입 in
    실행코드
}
```
```swift
// 함수는 이름이 있는 클로저
var sumFunction(a: Int, b: Int) -> Int {
    return a + b
}
var sum: (Int, Int) -> Int = { (a: Int, b:Int) in
    return a + b
}
print(sum(1, 2)) // 3

// 함수는 클로저의 일종이므로 할당 가능
sum = sumFunction(a:b:)
```

<br>

## 2. 함수의 전달인자로 사용
```swift
let add: (Int, Int) -> Int
add = { (a: Int, b: Int) -> Int in
    return a + b;
}

func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return method(a, b)
}

print(calculate(a: 1, b: 2, method: add)) // 3
```

<br>

## 3. 축약
축약을 너무 많이 하면, 다른사람이 알아보기 힘드니 주의

#### a. 후행 클로저
- 클로저가 함수의 마지막 전달인자면, 매개변수 이름 생략
```swift
func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return a + b
}

var result = calculate(a: 10, b: 10) {(left: Int, right: Int) -> Int in
    return left + right
}
```

<br>

#### b. 반환타입 생략
   - 어떤 타입을 반환할 것인지 컴파일러가 알고 있기 때문에, 생략 가능함
   - 대신 in 키워드는 생략 불가능
```swift
func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return a + b
}

var result = calculate(a: 10, b: 10) {(left: Int, right: Int) in
    return left + right
}
```

<br>

#### c. 단축 인자이름
- 클로저의 매개변수 이름이 필요하지 않으면, 단축 인자이름 사용
- 클로저의 매개변수 순서대로 $0, $1... 처럼 표현
```swift
func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return a + b
}

var result = calculate(a: 10, b: 10) {
    return $0 + $1
}
```

<br>

#### d. 암시적 반환 표현
- 클로저가 반환하는 값이 있다면, 클로저의 마지막 줄의 결과값은 반환값으로 취급
```swift
func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return a + b
}

var result = calculate(a: 10, b: 10) {
    $0 + $1
}
```