#### `rank`
If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the order of each element. If there are several equal equal elements, `rank` will return the median).
```
> rank(rank(c("dog", "cat", "sheep", "cow"))
[1] 3 1 4 2
``` 

#### `order`
To get a sorted list: which element should in you pick? In which `order`? 
(The function `order` returns the index each element would have if the list were sorted).
```
> order(c("dog", "cat", "sheep", "cow"))
[1] 2 4 1 3
```
And in general:
```
sort(x) == x[order(x)]
all(x==x[order(x)][rank(x)])
```

#### `dplyr::desc`
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
The function `dplyr::desc(x)` is the same as `-(rank(
```
dplyr::desc(c("dog", "cat", "sheep", "cow"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM3ODQ0OTAwOCwxNzQ0ODk1NTM2LC0xNj
k3NTA2MzM1LDE1NTkzOTI2MjcsLTYyODI5MTc5NSwtMTM2MDc1
NzEzNiwxOTAxMTgzODM5XX0=
-->