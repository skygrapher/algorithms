# 2D array - DS
* https://www.hackerrank.com/challenges/2d-array/problem

## Solution
### fdelpini
```kotlin
fun hourglassSum(arr: Array<Array<Int>>): Int {
    var sumList : ArrayList<Int> = arrayListOf()
    for(i in 0 .. 3) {
        for(j in 0 .. 3) {
            val sum = arr[i][j] + arr[i][j+1] + arr[i][j+2] +
                    arr[i+1][j+1] +
                    arr[i+2][j] + arr[i+2][j+1] + arr[i+2][j+2]
            sumList.add(sum)
        }
    }
    return sumList.max()!!
}
```
### 