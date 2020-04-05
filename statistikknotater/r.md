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
> order(c("c", "a", "d", "b", "a"))
[1] 2 5 4 1 3
```

#### `dplyr::desc`
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
```
desc2 <- function(x) { 
  if (class(x) %in% c("integer", "numeric")) {
    -x
  } else { 
    -rank(x, ties.method="min")
  }
}
```
Example:
```
> desc(c("c", "a", "d", "b", "a"))
[1] -4 -1 -5 -3 -1
> arrange(data.frame(x, stringsAsFactors="F"), desc(x))$x
[1] "d" "c" "b" "a" "a"
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzI1MTUwMzk0LC00Mzc5NTM3NjAsMTM1Mj
c5NjU3MSwtOTIzNzU4NTQsLTI4ODY4NzA4OCwxMTk2NzM3Njg2
LC0xMjA4OTkyODcwLDE3NDQ4OTU1MzYsLTE2OTc1MDYzMzUsMT
U1OTM5MjYyNywtNjI4MjkxNzk1LC0xMzYwNzU3MTM2LDE5MDEx
ODM4MzldfQ==
-->