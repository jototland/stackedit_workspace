If you were to sort a list, which `rank` would each element have?
(The function `rank` returns the order of each element).
```
> rank(rank(c("dog", "cat", "sheep", "cow"))
[1] 3 1 4 2
``` 
To get a sorted list: which element should in you pick? In which `order`? 
(The function `order` returns the index each element would have if the list were sorted).
```
> order(c("dog", "cat", "sheep", "cow"))
[1] 2 4 1 3

```
And in general:
```
rank(order(x)) == order(rank(x))
```
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
The function `dplyr::desc(x)` is the same as `-(rank(
```
dplyr::desc(c("dog", "cat", "sheep", "cow"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUxNzg4MzE1LC02MjgyOTE3OTUsLTEzNj
A3NTcxMzYsMTkwMTE4MzgzOV19
-->