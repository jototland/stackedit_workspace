#### `rank`
If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the order each element would have in a sorted list. If there are several equal equal elements, `rank` will return the median of the indices).
```
> rank(rank(c("dog", "cat", "sheep", "cow"))
[1] 3 1 4 2
``` 

#### `order`
To get a sorted list: which element should in you pick? In which `order`? 
(The function `order` returns the indices you should pick from the input list to get it in sorted order).
```
> sort(x) == x[order(x)]
```
Example:
> order(c("dog", "cat", "sheep", "cow"))
[1] 2 4 1 3
```
And in general:
```

all(x==x[order(x)][rank(x)])
```

#### `dplyr::desc`
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
The function `desc(x)` is the same as `-(rank(
```
desc(c("dog", "cat", "sheep", "cow"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMDcyMDAwNDcsLTEyMDg5OTI4NzAsMT
c0NDg5NTUzNiwtMTY5NzUwNjMzNSwxNTU5MzkyNjI3LC02Mjgy
OTE3OTUsLTEzNjA3NTcxMzYsMTkwMTE4MzgzOV19
-->