#### `rank`
If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the index position each element would have in a sorted list. If there are several equal equal elements, `rank` will return the average of the indices, unless `ties.method` is specified as something else).
```
all(sort(x)[rank(x)] == x) # non-integer indices will be truncated
```
Example:
```
> rank(rank(c("c", "a", "d", "b"))
[1] 3 1 4 2
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
all(desc(x) == -rank(x, ties.method="min"))
```
Example:
```
desc(c("c", "a", "d", "b"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE0MjA3MzczMSwtMjg4Njg3MDg4LDExOT
Y3Mzc2ODYsLTEyMDg5OTI4NzAsMTc0NDg5NTUzNiwtMTY5NzUw
NjMzNSwxNTU5MzkyNjI3LC02MjgyOTE3OTUsLTEzNjA3NTcxMz
YsMTkwMTE4MzgzOV19
-->