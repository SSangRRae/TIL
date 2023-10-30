# 03_컬렉션 타입

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 종류
1. Array: 순서가 있는 리스트
2. Dictionary: 키와 값의 쌍으로 이루어짐
3. Set: 순서가 없고, 멤버가 유일함

<br>

## 2. Array
```swift
var integers: Array<int> = Array<int>()

// 값 추가
integers.append(1)
integers.append(100)

// 값 확인
integers.contains(100) // true
integers.contains(999) // false

// 값 삭제
integers.remove(at: 0) // index에 해당하는 값 삭제
integers.removeLast() // 마지막 값 삭제
integers.removeAll() // 전체 삭제

// 개수 확인
integers.count
```

<br>

## 3. Dictionary
```swift
// String 타입 Key, Any 타입 Value
var anyDictionary: Dictionary<String, Any> = [String: Any]()

// 값 추가
anyDictionary["key1"] = "value1"
anyDictionary["key2"] = 2

// 값 삭제
anyDictionary.removeValue(forKey: "key")
anyDictionary["key2"] = nil
```

<br>

## 4. Set
```swift
var integerSet: Set<int> = Set<int>()

// 값 추가
integerSet.insert(1)
integerSet.insert(100)

// 값 확인
integerSet.contains(1) // true
integerSet.contains(2) // false

// 값 삭제
integerSet.remove(1)
integerSet.removeFirst()

// 개수 확인
integerSet.count
```

<br>

## 5. 리터럴 표기법
```swift
// Array
var doubles: Array<Double> = [Double]()
var strings: [String] = [String]()
var characters: [Character] = []

// Dictionary
var emptyDic: Dictionary[String, String] = [:]

// Set은 없음
```