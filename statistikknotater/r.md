`rank` gives the rank of each element, if they were sorted in order
```
> rank(rank(c("dog", "cat", "sheep", "cow"))
[1] 3 1 4 2
``` 
Which element should in you pick? In which `order`  (if you wanted them in `order`?)
```
> order(c("dog", "cat", "sheep", "cow"))
[1] 2 4 1 3
```
```
dplyr::desc(c("dog", "cat", "sheep", "cow"))
[1] -3 -1 -4 -2
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA1NDkzMTU0NV19
-->