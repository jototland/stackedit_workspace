#### `rank`
If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the index position each element would have in a sorted list. If there are several equal equal elements, `rank` will return the average of the indices, unless `ties.method` is specified as something else).
```
all(sort(x)[rank(x)] == x) # non-integer indices will be truncated
```
Example:
```
> rank(c("c", "a", "d", "b", "a"))
[1] 4.0 1.5 5.0 3.0 1.5
``` 

#### `order`
To get a sorted list: which element should in you pick? In which `order`? 
(The function `order` returns the indices you should pick from the input list to get it in sorted order).
```
all(sort(x) == x[order(x)])
```
Example:
```
> order(c("c", "a", "d", "b"))
[1] 2 4 1 3
```

#### `dplyr::desc`
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
```
all(desc(x) == if (class(x) %oin
```
Example:
```
desc(c("c", "a", "d", "b"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MTU5NTc3MTksLTkyMzc1ODU0LC0yOD
g2ODcwODgsMTE5NjczNzY4NiwtMTIwODk5Mjg3MCwxNzQ0ODk1
NTM2LC0xNjk3NTA2MzM1LDE1NTkzOTI2MjcsLTYyODI5MTc5NS
wtMTM2MDc1NzEzNiwxOTAxMTgzODM5XX0=
-->