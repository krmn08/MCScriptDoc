# Operator
MCScript can use all Java operators except unsigned right shift, increment, and decrement. In this section, we will discuss operators that are not in Java and that operate differently.
#### Floor division operator "//"
After normal division, round down after the decimal point.
```
Println(5d // 2) # 2
Println(1.5 // 1) # 1
```
#### Power operator "**"
Calculate the power.
```
Println(2 ** 8) # 256
Println(0 ** 0) # 1
```
//=, **= can also be used.
#### Equality operators "==" "!="
The equality operator is the equals method in Java.
```
Println("aaa" == String("aaa")) # true
Println("aaa" != String("aaa")) # false
```
#### Referential equality operators "is" "isnot"
The referential equality operator is equivalent to “==” in Java.
Since MCScript numbers are handled by the wrapper class, comparison with the reference equality operator is not possible.[^1]
```
Println(128 is 128) # false
Println(1d is 1d) # false
Println('a' is 'a') # false

a = null
Println(a is null) # true
Println(a isnot null) # false

a = true
Println(a is true) # true
```
#### Membership test operators "in" "notin"
If the right side is a collection, it is synonymous with contains. If it is a Map, it is synonymous with containsKey. In the case of an array, each element is looped and compared using the equals method.
```
list = [1, 2, 3]
Println(1 in list) # true
Println(1 notin list) # false

map = {"a":1, "b":2}
Println("a" in map) # true
Println(1 in map) # false

array = Array(int, 5)
array[3] = 1
Println(1 in array) # true
```
You can also determine if the number is within range.
```
Println(4 in 1..10) # true
Println(4 notin 5..1) # false
```
#### Null coalescing operator「?:」
If the left side is null, the right side is evaluated; otherwise, the left side is evaluated.
```
a = 1
Println(a ?: 2) # 1
a = null
Println(a ?: 2) # 2
```

[^1]: Java treats integers from -128 to 127 as the same object, so comparison with a reference equality operator is possible.