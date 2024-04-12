---
layout: post
title:  "Swift) Optional & Closure"
date:   2024-04-10
categories: Swift SwiftUI Xcode git macOS
---

Techit iOS appschool 5기 
Team6 study(1)

1. Optional

(1) Optional 이란? 

변수에 값이 있거나 없을 수 있음을 나타내주는 타입! 
nil 을 허용함으로써 프로그램에서 잠재적 오류를 방지 (nil ≈ null)

사용자의 이름 변수가 있다고 가정, 분명 이름을 입력하지 않은 nil 값이 있을 것임 
이때 ! optional type을 "?" 를 통해 선언해줌 

에시를 한번 보자 

```Swift
var userName: String? = "Yehjin" 
print(userName) //Optional("Yehjin")
```

userName은 String? 타입으로 선언됨. 이는 여기서 해당 변수가 문자열 일수도 nil값을 가질 수도 있다는 의미. 옵셔널 타입을 String? 으로 선언해주었기에 출력 값이 Optional wrapper 안에 있음으로 출력됨.


(2) Forced unwrapping 

강제 언래핑은 옵셔널에서 값을 강제로 추출하는 방법으로, 옵셔널이 nil값이 아님을 확실할 때 사용하게됨. nil일 경우에는 런타임 오류가 발생 .. 
> 래핑된 값을 옵서녈 타입에서 "!"를 통해 간단하게~ 언래핑해줄 수 있음 (우왕)

```Swift
var optionalNum: Int? = 123
var number = optionalNum! 
print(number) //123
```

optionalNum변수가 정수 타입(Int?)로 선언되었고 123이라는 값 할당됨. 
number 변수에 위의 optionalNum변수를 !로 강제 언래핑하여 실제 값을 추출해줌. 



(3) Optional Binding

옵셔널 바인딩을 사용하면 안전하게 옵셔널의 값을 추출 가능 

'if let' 또는 'guard let'을 사용하여 값이 'nil'인지 체크하고, 아닐 경우 지정된 블록 내에서 값을 사용 가능 

```Swift
var optionalStr: String? = "Hello, yehjin!"
if let string = optionalStr {
    print(string) // Hello, yehjin!
} else {
    print("no value")
}
```

위의 코드에서는 'if let' 구문을 통해 'optionalStr'이 nil 값이 아니라면 그 값을 string이라는 새로운 변수로 할당하고, 출력해줌. nil값인지 아닌지를 아는 것이 중요하기 때문에 이걸 쓰는 듯함 만약 모르고 그냥 하면? 런타임에러가 나겠죠.. 


2. Closure 

클로저는 코드 블록을 변수에 저장하거나 다른 함수에 인자로 전달할수 있게 해주는 기능 
> 함수의 기능을 하지만 함수처럼 안 생김 + 여러가지로 쓰임새가 많은 함수 
+ 주변 context의 변수를 캡처할 수 있음 

```Swift
let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
let reversedNames = names.sorted(by: { (s1: String, s2: String) -> Bool in
    return s1 > s2
})
print(reversedNames) // ["Ewa", "Daniella", "Chris", "Barry", "Alex"]

```

클로저를 사용하여 문자열(이름들) 배열을 정렬하는 방법을 정의해봄. 
위의 코드에서 두 문자열을 비교하여 bool값을 반환하는 클로저를 인자로 받아서 s1이 s2 보다 크면  true, 아니면 false 를 반환하게 하여 내림차순으로 정렬해줌. 


```Swift
func functionA() -> () -> Int {
    var count = 0 
    func functionB() -> Int {
        return counter + 10 
  }
  return functionB
}
let myClosure = functionA()
let result = myClosure()

```
예제를 하나 더 보자. 
위의 코드에서 functionA 는 B를 반환한다. 사실 functionB는 내부영역 밖에 선언된 counter 변수에 의존하기에 functionA는 클로저를 반환하고 있는 구조이다. 다시 말해서, functionB는 counter변수를 잡고(captured) 있다. 그래서 클로저 



