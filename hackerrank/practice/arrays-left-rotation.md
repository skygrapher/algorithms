# Arrays: Left Rotation
* https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem

## Solution
### fdelpini
#### First solution
``` kotlin
fun rotLeft(a: Array<Int>, d: Int): Array<Int> {
    var result : Array<Int> = Array(a.size, {0})
    for(i in 0 until a.size) { // 4 -> 0 -> 1 -> 2 -> 3
        result[i] = a[(d + i) % a.size]
    }
    return result
}
```
#### Using array constructor
```kotlin
fun rotLeft(a: Array<Int>, d: Int): Array<Int> {
    return Array(a.size, { i -> a[(d + i) % a.size]})
}
```