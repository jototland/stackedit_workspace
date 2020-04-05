#### `rank`
If you were to sort a list, which `rank` would each element have?

The function `rank` returns the index position each element would have in a sorted list. If there are several equal equal elements, `rank` will return the average of the indices, unless `ties.method` is specified as something else.

* ties.method="min" : the lowest possible index will be used for all equal values
* ties.method="max": the highest possible index will be used all equal values
* ties.method="first": indices for equal values will be in same order as occurrence in input
* ties.method="last": indices for equal values will be in reverse order of occurrence in input
* ties.method="average": indices will be the average of "min" and "max" (the default)
* ties.method="random": indices for equal values will in random order

For any input vector `x`, `all(sort(x)[rank(x)] == x)` will return `TRUE`.

Example:
```
> rank(c("c", "a", "d", "b", "a"))
[1] 4.0 1.5 5.0 3.0 1.5
``` 

#### `order`
To get a sorted list: which element should in you pick? In which `order`? 

The function `order` returns the indices you should pick from the input list to get it in sorted order.

For any input vector `x`, `all(sort(x) == x[order(x)])` will return `TRUE`.

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
#### `nest` and `unnest`
```
df %>% nest(data=-c(remaining columns)) -> dfn
dfn %>% unnest(cols=data) -> df
dfn$data[[rownumber]]
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk4ODMwNjExNywxMzQyNzY3MDI0LC03MD
cyMjc5MDAsLTE0MDQyMTAyMTEsNzI1MTUwMzk0LC00Mzc5NTM3
NjAsMTM1Mjc5NjU3MSwtOTIzNzU4NTQsLTI4ODY4NzA4OCwxMT
k2NzM3Njg2LC0xMjA4OTkyODcwLDE3NDQ4OTU1MzYsLTE2OTc1
MDYzMzUsMTU1OTM5MjYyNywtNjI4MjkxNzk1LC0xMzYwNzU3MT
M2LDE5MDExODM4MzldfQ==
-->