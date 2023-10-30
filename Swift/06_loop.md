# 06_반복문

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. for-in
```swift
var nums = [1, 2, 3]
let dic = ["apple": 1, "banana": 2, "cherry": 3]

for num in nums {
    print(num)
}

for (fruit, num) in dic {
    print("\(fruit): \(num)")
}
```

<br>

## 2. while
```swift
var nums = [1, 2, 3]

while nums.count > 1 {
    nums.removeLast()
}
```

<br>

## 3. repeat-while
```swift
var nums = [1, 2, 3]

repeat {
    nums.removeLast()
} while nums.count > 0
```