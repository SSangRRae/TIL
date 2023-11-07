# 11_값, 참조 타입

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 값 타입
- 데이터를 전달할 때, 값을 복사하여 전달
- 종류
   - Struct
   - Enum
```swift
struct ValueType {
    var property = 1
}

let firstStructInstance = ValueType()
var secondStructInstance = firstStructInstance
secondStructInstance.property = 2

print(firstStructInstance.property) // 1
print(secondStructInstance.property) // 2
```
<br>

## 2. 참조 타입
- 데이터를 전달할 때, 값의 메모리 위치를 전달
- 종류
   - Class
```swift
class ReferenceType {
    var property = 1
}

let firstClassInstance = ReferenceType()
var secondClassInstance = firstClassInstance
secondClassInstance.property = 2

print(firstClassInstance.property) // 2
print(secondClassInstance.property) // 2
```