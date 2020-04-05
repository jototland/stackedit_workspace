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
desc2 <- function(x) if (class(x) %in% c("integer", "numeric")) -x 
else -rank(x, ties.method="min")
```
Example:
```
desc(c("c", "a", "d", "b"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE3MTk5Njc0OCwxMzUyNzk2NTcxLC05Mj
M3NTg1NCwtMjg4Njg3MDg4LDExOTY3Mzc2ODYsLTEyMDg5OTI4
NzAsMTc0NDg5NTUzNiwtMTY5NzUwNjMzNSwxNTU5MzkyNjI3LC
02MjgyOTE3OTUsLTEzNjA3NTcxMzYsMTkwMTE4MzgzOV19
-->