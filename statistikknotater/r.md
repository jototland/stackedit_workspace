#### `rank`
If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the index position each element would have in a sorted list. If there are several equal equal elements, `rank` will return the average of the indices, unless `ties.method` is specified).
```
> rank(rank(c("c", "a", "d", "b"))
[1] 3 1 4 2
``` 

#### `order`
To get a sorted list: which element should in you pick? In which `order`? 
(The function `order` returns the indices you should pick from the input list to get it in sorted order).
```
> sort(x) == x[order(x)]
```
Example:
```
> order(c("c", "a", "d", "b"))
[1] 2 4 1 3
```
And in general:
```
all(x==x[order(x)][rank(x)])
```

#### `dplyr::desc`
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
The function `desc(x)` is the same as `-(rank(x))`
```
desc(c("c", "a", "d", "b"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjczNzE4OTQzLDExOTY3Mzc2ODYsLTEyMD
g5OTI4NzAsMTc0NDg5NTUzNiwtMTY5NzUwNjMzNSwxNTU5Mzky
NjI3LC02MjgyOTE3OTUsLTEzNjA3NTcxMzYsMTkwMTE4MzgzOV
19
-->