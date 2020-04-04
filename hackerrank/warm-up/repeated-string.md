# Repeated String
* https://www.hackerrank.com/challenges/repeated-string/problem

## Solution
### fdelpini
```kotlin
fun repeatedString(s: String, n: Long): Long {
    var count : Long = 0
    for(i in 0 until s.length) {
        if(s[i] == 'a') count++
    }
    var result : Long = (n / s.length) * count
    val lastString = s.substring(0, (n % s.length).toInt())
    for(i in 0 until lastString.length) {
        if(lastString[i] == 'a') result++
    }

    return result
}
```
### 