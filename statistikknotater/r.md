#### `rank`
If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the index position each element would have in a sorted list. If there are several equal equal elements, `rank` will return the average of the indices, unless `ties.method` is specified as something else).

Example:
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
```
all(desc(x) == -rank(x, ties.method="min"))
```
Example:
```
desc(c("c", "a", "d", "b"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI4ODY4NzA4OCwxMTk2NzM3Njg2LC0xMj
A4OTkyODcwLDE3NDQ4OTU1MzYsLTE2OTc1MDYzMzUsMTU1OTM5
MjYyNywtNjI4MjkxNzk1LC0xMzYwNzU3MTM2LDE5MDExODM4Mz
ldfQ==
-->