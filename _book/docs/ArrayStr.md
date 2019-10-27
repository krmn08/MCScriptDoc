# Array, String

## Array
Arrays are basically deprecated in MCScript. Basically, you should use lists and convert arrays from lists only when you need them. There is little advantage to using arrays with MCScript.

#### Create array
Use the Array function to create an array. Each element is initialized with the Java default value[^1].
```
array = Array(int, 10)
```
To convert a list to an array, pass the list as the second argument.
```
list = [1, 2, 3]
array = Array(int, list)
```
If you want to convert the data, pass a function as the third argument.
```
list = ["abcd", "efg", "hi"]
array = Array(int, list, fun(s): s.length)
array # [4, 3, 2]
```
#### Access elements
Access to elements is the same as Java, except that you can specify negative values.
```
array = Array(int, [1, 2, 3])
array[0] = 0
array[-1] = 4
array # [0, 2, 4]
```
#### Get array length
To get the length of an array, use the Length function.
```
array = Array(int, [1, 2, 3])
Length(array) # 3
```
## String manipulation
You can treat strings like immutable character arrays.
```
str = "hello"
str[0] # h
str[-1] # o
```
You can also cut out a specified range like a list.
```
str = "hello"
str[1:4] # ell
str[3:] # lo
str[:2] # he
str[:] # hello
```
[^1]: The basic numeric type is initialized to 0, char is '\ u0000', boolean is false, and the reference type is null.