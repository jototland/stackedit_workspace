If you were to sort a list, which `rank` would each element have?
```
> rank(rank(c("dog", "cat", "sheep", "cow"))
[1] 3 1 4 2
``` 
To get a sorted list: which element should in you pick? In which `order`? 
```
> order(c("dog", "cat", "sheep", "cow"))
[1] 2 4 1 3
```
If you were to sort a dataframe in `desc`ending order, how would you transform the input vector?
```
dplyr::desc(c("dog", "cat", "sheep", "cow"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk1NzM1NDI1MV19
-->