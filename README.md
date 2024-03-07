/*
 Lv1
 더하기, 빼기, 나누기, 곱하기 연산을 수행할 수 있는 Calculator 클래스를 만들기
 생성한 클래스를 이용하여 연산을 진행하고 출력
*/
class Calculator {
    //더하기
    func add(_ a: Int, _ b: Int) -> Int {
        return a + b
    }
    //빼기
    func sub(_ a: Int, _ b: Int) -> Int {
        return a - b
    }
    //곱하기
    func mul(_ a: Int, _ b: Int) -> Int {
        return a * b
    }
    //나누기
    func div(_ a: Int, _ b: Int) -> Int {
        return a / b
    }
}

let calculator = Calculator()
calculator.add(1, 2)
calculator.sub(3, 4)
calculator.mul(5, 6)
calculator.div(10, 2)


/*
 Lv2
 Lv1에서 만든 Calculator 클래스에 “나머지 연산”이 가능하도록 코드를 추가하고, 연산 진행 후 출력
 ex) 나머지 연산 예시 : 6을 3으로 나눈 나머지는 0 / 5를 3으로 나눈 나머지는 2
*/
class Calculator {
    //더하기
    func add(_ a: Int, _ b: Int) -> Int {
        return a + b
    }
    //빼기
    func sub(_ a: Int, _ b: Int) -> Int {
        return a - b
    }
    //곱하기
    func mul(_ a: Int, _ b: Int) -> Int {
        return a * b
    }
    //나누기
    func div(_ a: Int, _ b: Int) -> Int {
        return a / b
    }
    //나머지
    func remainder(_ a: Int, _ b: Int) -> Int {
        return a % b
    }
}

let calculator = Calculator()
calculator.add(1, 2)
calculator.sub(3, 4)
calculator.mul(5, 6)
calculator.div(10, 2)
calculator.remainder(5, 3)

import UIKit

/*
 Lv3
 아래 각각의 클래스들을 만들고 클래스간의 관계를 고려하여 Calculator 클래스와 관계 맺기
 - AddOperation(더하기)
 - SubstractOperation(빼기)
 - MultiplyOperation(곱하기)
 - DivideOperation(나누기)
 Calculator 클래스의 내부코드를 변경
 - 관계를 맺은 후 필요하다면 별도로 만든 연산 클래스의 인스턴스를 Calculator 내부에서 사용
 - Lv2 와 비교하여 어떠한 점이 개선 되었는지 스스로 생각해 봅니다.
     - hint. 클래스의 책임(단일책임원칙)
*/
/*
class Calculator {
    func cal(_ sign :Character, _ a: Int, _ b: Int) -> Int {
        switch sign {
        case "+":
            return a + b
        case "-":
            return a - b
        case "*":
            return a * b
        case "/":
            return a / b
        case "%":
            return a % b
        default:
            return 0
        }
    }
}

//더하기
class AddOperation: Calculator {
    override func cal(_ sign: Character = "+", _ a: Int, _ b: Int) -> Int {
        return super.cal(sign, a, b)
    }
}

let addOperation = AddOperation()
addOperation.cal(10, 20)
*/

class Calculator {
    let addOper = AddOperation()
    let subOper = SubstractOperation()
    let multiOper = MultiplyOperation()
    let divOper = DivideOperation()
    let remainOper = RemainderOperation()
}

//더하기
class AddOperation {
    //더하기
    func add(_ a: Int, _ b: Int) -> Int {
        return a + b
    }
}
//빼기
class SubstractOperation {
    //빼기
    func sub(_ a: Int, _ b: Int) -> Int {
        return a - b
    }
}
//곱하기
class MultiplyOperation {
    //곱하기
    func mul(_ a: Int, _ b: Int) -> Int {
        return a * b
    }
}
//나누기
class DivideOperation {
    //나누기
    func div(_ a: Int, _ b: Int) -> Int {
        return a / b
    }
}
//나머지
class RemainderOperation {
    //나머지
    func remainder(_ a: Int, _ b: Int) -> Int {
        return a % b
    }
}
let cal = Calculator()
print(cal.addOper.add(10, 20))
print(cal.subOper.sub(10, 20))
print(cal.multiOper.mul(10, 20))
print(cal.divOper.div(10, 20))
print(cal.remainOper.remainder(10, 20))


/*
 Lv4
 - AbstractOperation라는 **추상화된** 클래스를 만들기
 - 기존에 구현한 AddOperation(더하기), SubtractOperation(빼기), MultiplyOperation(곱하기), DivideOperation(나누기) 클래스들과 관계를 맺고 Calculator 클래스의 내부 코드를 변경
 - 스위프트의 어떤 문법을 이용하여 추상화할 수 있을지 생각해 봅시다
 - Lv3 와 비교해서 어떠한 점이 개선 되었는지 스스로 생각해 봅니다.
     - hint. 클래스간의 결합도, 의존성(의존성역전원칙)
 */
class AbstractOperation {
    func cal() {
        print("추가")
    }
}

//더하기
class AddOperation: AbstractOperation {
    override func cal() {
        print("계산로직 추가")
    }
    //부모 클래스 메서드 오버로딩
    func cal(_ a: Int, _ b: Int) -> Int {
        return a + b
    }
}
//빼기
class SubstractOperation: AbstractOperation {
    override func cal() {
        print("계산로직 추가")
    }
    //부모 클래스 메서드 오버로딩
    func cal(_ a: Int, _ b: Int) -> Int {
        return a - b
    }
}
//곱하기
class MultiplyOperation: AbstractOperation {
    override func cal() {
        print("계산로직 추가")
    }
    //부모 클래스 메서드 오버로딩
    func cal(_ a: Int, _ b: Int) -> Int {
        return a * b
    }
}
//나누기
class DivideOperation: AbstractOperation {
    override func cal() {
        print("계산로직 추가")
    }
    //부모 클래스 메서드 오버로딩
    func cal(_ a: Int, _ b: Int) -> Int {
        return a / b
    }
}
//나머지
class RemainderOperation: AbstractOperation {
    override func cal() {
        print("계산로직 추가")
    }
    //부모 클래스 메서드 오버로딩
    func cal(_ a: Int, _ b: Int) -> Int {
        return a % b
    }
}

let addOperation = AddOperation()
addOperation.cal(10, 20)
let substractOperation = SubstractOperation()
substractOperation.cal(10, 20)
let multiplyOperation = MultiplyOperation()
multiplyOperation.cal(10, 20)
let divideOperation = DivideOperation()
divideOperation.cal(10, 20)
let remainerOper = RemainderOperation()
remainerOper.cal(10, 20)
