# Java
MCScript is a scripting language that runs on Java. Every object in MCScript is also a Java object.
MCScript can handle Java objects in the same way as Java. The syntax is the same as Java, such as method calls and field access.

This section describes MCScript-specific features in addition to basic Java syntax.
## Import Class
Like Java, you can import classes with the import statement.
```
import java.util.Calendar
```
In the above, ClassObject is assigned to `Calender` constant.
```
const Calendar = java.util.Calendar
Calender # ClassObject class
Calender.class # Calendar class
```
## Creating Objects
Unlike Java, there is no need to add new when creating an object.
```
vector = Vector(0, 0, 0)
```
## Method Call
In MCScript, you can specify a type as an argument when calling a method.
In this case, it will not run unless the types match exactly.
```java
void call(String pre, String s) {
    System.out.println(pre + "String");
}
void call(String pre, Object o) {
    System.out.println(pre + "Object");
}
```
```
call("class: ", "string": Object) # class: Object
```
If you want to expand the array as an argument and pass it, use vararg.
```java
void call(int... args) {
    System.out.println(Arrays.toString(args));
}
void call(String str, int i) {
    System.out.println(str + i);
}
```
```
array = Array(int, 5);
for (i in Until(5)) {
    array[i] = i;
}
call(vararg array)

array = Array(Object, ["abc", 3])
call(vararg array)
```
## Property
MCScript implements a feature called properties.
Properties are feature that hide getters and setters.
Although it seems to be accessing the field, getter and setter are called internally.
```
vector = Vector(0, 1, 2)
vector.x = 1
vector.y = vector.z
vector.z = 3
vector # Vector(1, 2, 3)
```
If any of get, is, or set is prepended to the method name, the property function can be used.
Converts all uppercase letters at the beginning of the property name to lowercase.
```
player = getPlayer("PlayerName")
player.displayName # PlayerName
```
## Unsafe Access
By adding an exclamation after the member name, it becomes possible to access members that are not accessible.
```java
class Test {
    private int i = 1;

    private Test() {}

    private void call() {
        System.out.println("test");
    }
}
```
```
test = Test!()
Println(test.i!) # 1
Println(test.call!()) # test
```
When accessing a field, it operates faster than the property, but use it with caution because it is a dangerous operation.
## Extention Function
In MCScript, you can extend an existing class to add methods.
Inside the function, the receiver object is passed to `this` constant.
```
fun String.count(ch) {
    count = 0
    for c in this.toCharArray() {
        if (c == ch) {
            count += 1
        }
    }
    count
}

"ababababa".count('a') # 5
```
Extension functions are available from all scopes.
## Functional Interface
Since MCScript cannot define a class, it cannot implement a functional interface. Instead, if the argument type is a functional interface, the MCScript function object is converted to a functional interface.
```
list = ["abc", "defg", "hijkl"]
list.stream()\
        .map(s -> s.length())\
        .forEach(Println)
/*
3
4
5
*/
```
Java methods are converted in the same way.
```
list = ["abc", "defg", "hijkl"]
list.stream()\
        .map(s -> s.toUpperCase())\
        .forEach(System.out.println)
/*
ABC
DEFG
HIJKL
*/
```