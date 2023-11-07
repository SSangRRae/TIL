# 22_고차함수

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- 전달인자로 함수를 전달받거나 함수 실행 결과를 함수로 반환하는 함수
- map, filter, reduce

<br>

## 2. map
- 컨테이너 내부의 기존 데이터를 변형하여 새로운 컨테이너 생성
```swift
let numbers: [Int] = [0, 1, 2, 3, 4]
var doubledNumbers: [Int]
var Strings: [String]

doubledNumbers = [Int]()
strings = [String]()

doubledNumbers = numbers.map({ (number: Int) -> Int in
    return number * 2
})

strings = numbers.map({ 
    (number: Int) -> String in
    return "\(number)"
})

// 매개변수, 반환 타입, 반환 키워드 생략, 후행 클로저
doubledNumbers = numbers.map { $0 * 2 }
```

<br>

## 3. filter
- 컨테이너 내부의 값을 걸러서 새로운 컨테이너로 추출
```swift
let numbers: [Int] = [0, 1, 2, 3, 4]
var filtered: [Int] = [Int]()

let evenNumbers: [Int] = numbers.filter {
    (number: Int) -> Bool in

    return number % 2 == 0
}

// 후행 클로저
let oddNumbers: [Int] = numbers.filter {
    $0 % 2 != 0
}
```

<br>

## 4. reduce
- 컨테이너 내부의 콘텐츠를 하나로 통합
```swift
let someNumbers: [Int] = [2, 8, 15]

// 초기값이 0이고 someNumbers 내부의 모든 값을 더합니다.
let sum: Int = someNumbers.reduce(0, {
    (first: Int, second: int) -> Int in
    return first + second
})

// 초기값이 0이고 someNumbers 내부의 모든 값을 뺍니다.
let subtract: Int = someNumbers.reduce(0, {
    (first: Int, second: Int) -> Int in
    return first - second
})

// 최값이 3이고 someNumbers 내부의 모든 값을 더합니다.
let sumFromThree = someNumbers.reduce(3) {
    $0 + $1
}
```