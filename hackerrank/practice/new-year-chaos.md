# New Year Chaos
* https://www.hackerrank.com/challenges/new-year-chaos/problem

## Solution
### fdelpini
```kotlin
```

### skygrapher
```swift
/// 해결전략.
/// n 부터 1 순서로 진행(큰 수부터 작은수 순서로)
/// 해당 숫자가 제자리에 없다면, 2번 이내에서 해당 숫자를 뒤쪽의 숫자와 자리를 교체한다.
/// 2번까지 교체했는데도 제자리에 없다면 Too chaotic 에러.
/// O(n²) - 해당 숫자의 index를 찾느라 n². 이부분을 커스텀하게 만들면 O(4n)정도로 최적화 가능. 해당 숫자는 n-2...n 사이에 있어야 하고 그렇지 않으면 too chatic 상황이라서.


/// 배열에서 해당 넘버가 제 자리에 위치해 있는가?
func isProperPosition(q: [Int], number: Int) -> Bool {
    guard number >= 1 && number <= q.count else { fatalError() }
    return q[(number - 1)] == number
}

let maxMove = 2 // 최대 2번까지만 움직일 수 있음.(최대 뇌물 주는 회수랑 같음.)

/// 입력으로 받은 배열을 순차적인 배열로 변경하면서 swap한 회수를 리턴한다. swap제한을 넘어가면 nil 리턴.(too chatic 상황)
func recoverChaos(q: [Int]) -> Int? {
    var recovered = q
    var stepCount = 0
    for number in (1...q.count).reversed() {
        for _ in 0..<maxMove {
            if !isProperPosition(q: recovered, number: number) {
                stepCount += 1
                guard let index = recovered.firstIndex(of: number) else { fatalError() }
                recovered.swapAt(index, index+1)
            }
        }
        if !isProperPosition(q: recovered, number: number) {
            return nil
        }
    }
    return stepCount
}

// Complete the minimumBribes function below.
func minimumBribes(q: [Int]) -> Void {
    guard let step = recoverChaos(q: q) else { print("Too chaotic"); return }
    print("\(step)")
}

```
