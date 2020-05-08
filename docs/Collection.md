# List, Map, YAML
## List
Create a list with a list literal.
```
list = [1, 2, 3]
list = [
    1,
    2,
    3
]
list = []
```
MCScript lists are implemented with ArrayList. You can call and manipulate methods, but MCScript is more intuitive.
#### Access Elements
In Java, you use get or set methods to access elements, but in MCScript you can access lists with subscripts, like arrays.
You can also specify the index from the back by specifying a negative value for the subscript. This behavior also applies to array and string subscripts.

```
list = [1, 2, 3]
list[1] # 2
list[1] = 1
list # [1, 1, 3]
```
#### Add/Remove Elements
You can do this efficiently by using the built-in functions Add and Remove.
```
list = ["abc", "def"]
Add(list, "ghi")
Remove(list, 1)
Remove(list, "abc")
list # ["ghi"]
```
#### Select a Elements of List
In MCScript, you can select a range of lists with subscripts. Internally, it makes use of the subList, so a reference to the original list is preserved.
```
list = [1, 2, 3]
list[1:3] # [2, 3]
list[0:0] # []
```
You can also omit the subscript.
```
list = [1, 2, 3]
list[1:] # [2, 3]
list[:2] # [1, 2]
list[:] # [1, 2, 3]
```
#### Delete Part of List
You can also use a range selection in the list to delete a selection.
```
list = [1, 2, 3]
list[1:].clear()
list # [1]
```
## Map
Create a map with a map literal.
```
map = {1:"a", 2:"b", 3:"c"}
map = {
    1:"a",
    2:"b",
    3:"c"
}
map = {}
```
MCScript maps are implemented in LinkedHashMap, so they preserve the insertion order. Like the list, it provides some useful syntax.
#### Access Map
Like the list, you can access the map by subscript. This works the same as get and put in Java.
```
map = {1:"a", "2":"b", obj:"c"}
map[1] # a
map["2"] # b
map[obj] # c

map[obj] = "object"
```
If the key is a character string, you can access it with a dot.
```
map = {}
map.a = 1
map # {"a":1}
map.a # 1
```
## YAML
In MCScript, YamlConfiguration can be handled like a map.

plugins/MCScript/test.yml
```yml
a: 1
ab:
  cd:
    ef: "2"
list:
  - 1
  - 2
  - 3
n:
```
```
path = "plugins/MCScript/test.yml"
yaml = Load(path) # YamlConfiguration.load(new File(path))
yaml["a"] + 1 # 2
yaml["a"] = 0
yaml["ab"]["cd"]["ef"] + 1 # 21
yaml["ab"]["cd"]["ef"] = 3

yaml.ab.cd.ef + 1 # 4
yaml.list.add(4)
yaml.list[0] = 0

yaml.list # [0, 2, 3, 4]

yaml.n ?: "none" # none

yaml.save(path)
```
