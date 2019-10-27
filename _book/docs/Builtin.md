# Builtin Function

|Name|Arguments|Description|
|---|---|---|
|Print|Object|Output an object to console|
|Println|Object|Output an object to the console and start a new line|
|ToString|Object|ToString corresponding to multi-dimensional array|
|Cast|ClassObject, Number|Cast number to specified type|
|Int|Character|Cast Character to Integer|
|Char|Integer|Cast Integer to Character|
|Array|ClassObject, Integer...|Creates an array with the specified type and size for each dimension|
|Array|ClassObject, List|Converts a list to an array of the specified type|
|Array|ClassObject, List, Function|Convert a list to an array of a specified type using a function|
|Add|Collection, Object|Add elements to the collection|
|Remove|List, Integer|Removes the element at the specified index from the list|
|Remove|Collection, Object|Removes the specified element from the collection|
|Length|Object|Get the length of an array or string|
|Field|Object|Returns a map of property names and values. If a ClassObject is passed, return a map of property names and value types|
|Iota|Integer|Initializes the internal value of Iota with the specified value and returns the value|
|Iota|-|Returns an incremented internal value of Iota|
|Load|String|Returns the YamlConfiguration of the specified file|
|ExecTime|Function|Returns the execution time of the specified function (ms)|