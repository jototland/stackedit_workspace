#### `rank`
If you were to sort a list, which `rank` would each element have?

The function `rank` returns the index position each element would have in a sorted list. If there are several equal equal elements, `rank` will return the average of the indices, unless `ties.method` is specified as something else.

* ties.method="min" : the lowest possible index will be used for all equal values
* ties.method="max": the highest possible index will be used all equal values
* ties.method="first": indices for equal values will be in same order as occurence
* ties.method="last": indices for equal values will be in reverse order of occurence
* ties.method="average": (the default)
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

The function `order` returns the indices you should pick from the input list to get it in sorted order.
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
eyJoaXN0b3J5IjpbLTk0NjQ5Njk2Nyw3MjUxNTAzOTQsLTQzNz
k1Mzc2MCwxMzUyNzk2NTcxLC05MjM3NTg1NCwtMjg4Njg3MDg4
LDExOTY3Mzc2ODYsLTEyMDg5OTI4NzAsMTc0NDg5NTUzNiwtMT
Y5NzUwNjMzNSwxNTU5MzkyNjI3LC02MjgyOTE3OTUsLTEzNjA3
NTcxMzYsMTkwMTE4MzgzOV19
-->