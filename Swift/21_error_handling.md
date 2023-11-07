# 21_오류처리

>[유튜브 yagom - 스위프트 기초문법 강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

<br>

## 1. 개념
- `Error 프로토콜`과 주로 열거형을 통해서 오류를 표현
- 오류 발생의 여지가 있는 메서드는 `throws`를 사용하여 오류를 내포하는 함수임을 표시
```swift
enum VendingMachineError: Error {
    case invalidInput
    case insufficientFunds(moneyNeeded: Int)
    case outOfStock
}

class VendingMachine {
    let itemPrice: Int = 100
    var itemCount: Int = 5
    var deposited: Int = 0

    // 돈 받기 메서드
    func receiveMoney(_ money: Int) throws {
        // 입력한 돈이 0 이하면 오류를 던짐
        guard money > 0 else {
            throw VendingMachineError.invalidInput
        }

        self.deposited += money
        print("\(money)원 받음")
    }

    // 물건 팔기 메서드
    func vend(numberOfItems numberOfItemsToVend: Int) throws -> String {
        // 원하는 아이템의 수량이 잘못 입력되었으면 오류
        guard numberOfItemsToVend > 0 else {
            throw VendingMachineError.invalidInput
        }

        // 구매하려는 수량보다 미리 넣어둔 돈이 적으면 오류
        guard numberOfItemsToVend * itemPrice <= deposited else {
            let moneyNeeded: Int
            moneyNeeded = numberOfItemsToVend * itemPrice - deposited

            throw VendingMachineError.insufficientFunds(moneyNeeded: moneyNeeded)
        }

        // 구매하려는 수령보다 요구하는 수량이 많으면 오류
        guard itemCount >= numberOfItemsToVend else {
            throw VendingMachineError.outOfStock
        }

        let totalPrice = numberOfItemsToVend * itemPrice

        self.deposited -= totalPrice
        self.itemCount -= numverOfItemsToVend

        return "\(numberOfItemsToVend)개 제공"
    }
}
```

<br>

## 2. 오류 처리
- 오류발생의 여지가 있는 throws 함수는 `try`를 사용하여 호출
- 오류발생의 여지가 있는 throws 함수는 `do-catch` 구문을 사용하여 오류발생에 대비
```swift
let machine: VendingMachine = VendingMachine()
var result: String?

do {
    try machine.receiveMoney(0)
} catch VendingMachineError.invalidInput {
    print("입력이 잘못되었습니다.")
} catch VendingMachineError.insufficientFunds(let moneyNeeded) {
    print("\(moneyNeeded)원이 부족합니다.")
} catch VendingMachineError.outOfStock {
    print("수량이 부족합니다.")
}

do {
    result = try machine.vend(numverOfItems: 4)
} catch {
    print(error)
}
```

<br>

- `try?`
   - 별도의 오류처리 결과를 통보받지 않고 오류가 발생했으면 nil로 반환
   - 정상동작 후에는 옵셔널 타입으로 정상 반환값을 돌려 받음
```swift
let machine: VendingMachine = VendingMachine()
var result: String?

result = try? machine.vend(numberOfItems: 2)
result // Optional("2개 제공")

result = try? machine.vend(numberOfItems: 2)
result // nil
```

<br>

- `try!`
   - 오류가 발생하지 않을 것이라는 강력한 확신을 가질 때 사용하면, 정상동작 후 결과값을 돌려 받음
   - 하지만, 오류가 발생하면 런타임 오류가 발생하여 애플리케이션 동작 중지
```swift
let machine: VendingMachine = VendingMachine()
var result: String?

result = try! machine.vend(numberOfItems: 1)
result // 1개 제공

// 런타임 오류
// result = try! machine.vend(numberOfItems: 1)
```