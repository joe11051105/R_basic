# 資料合併與分割

資料整理最後來介紹如何合併與分割資料。

+ union、cbind 與 rbind 函數
+ merge 函數
+ split 函數
+ subset 函數

### 資料合併

```r
> x <- c(1, 2, 3)
> y <- c(10, 20, 30)
> union(x ,y) # union 如英文名稱就是取聯集。
[1]  1  2  3 10 20 30

> rbind(x, y) # 透過 row 合併。
  [,1] [,2] [,3]
x    1    2    3
y   10   20   30

> cbind(x, y) # 透過 column 合併。
     x  y
[1,] 1 10
[2,] 2 20
[3,] 3 30

> x <- cbind(c("Tom", "Joe", "Vicky"), c(27, 29, 28))
> y <- cbind(c("Tom", "Joe", "Vicky"), c(178, 186, 168))
> colnames(x) <- c("name", "age")
> colnames(y) <- c("name", "tall")

> merge(x, y, by = "name") # 將 data.frame 透過一個欄位進行合併。
   name age tall
1   Joe  29  186
2   Tom  27  178
3 Vicky  28  168

> x <- cbind(c("Tom", "Joe", "Vicky", "Bob"), c(27, 29, 28, 25))
> y <- cbind(c("Tom", "Joe", "Vicky", "Bruce"), c(178, 186, 168, 170))
> colnames(x) <- c("name", "age")
> colnames(y) <- c("name", "tall")

> merge(x, y, by = "name", all = T) # alt 是用來詢問是否顯示所有資料，像 Bob 與 Bruce 都有一欄資料沒有，所以沒下 all = T，應該不會出現 Bob 與 Bruce 資料。
   name  age tall
1   Bob   25 <NA>
2   Joe   29  186
3   Tom   27  178
4 Vicky   28  168
5 Bruce <NA>  170

> merge(x, y, by = "name", all.x = T) # 只顯示 x 有的資料，所以 Bruce 就不會出現。
   name age tall
1   Bob  25 <NA>
2   Joe  29  186
3   Tom  27  178
4 Vicky  28  168

> merge(x, y, by = "name", all.y = T) # 只顯示 y 有的資料，所以 Bob 就不會出現。
   name  age tall
1   Joe   29  186
2   Tom   27  178
3 Vicky   28  168
4 Bruce <NA>  170
```

### 資料分割

```r
> data <- iris
> split(data, sample(rep(1:2, 75))) # rep(1:2, 75) 產生 1,2 交錯的向量，但加了前面的 sample 則是隨機抽取，所以向量 1,2 會被打亂，split 會依照 sample(rep(1:2, 75)) 分組，都是 1 的會在同一組，都是 2  的也會在同一組。

> data <- iris

> subset(data, Sepal.Length > 5) # 只會出現 Sepal.Length > 5 的資料

> subset(data, Sepal.Length > 5,select = Sepal.Length) # 只會出現 Sepal.Length > 5 的資料且欄位只有 Sepal.Length，select 代表會出現的欄位。

> subset(data, Sepal.Length > 5,select = -Sepal.Length) # selct = 負的代表不要出現的欄位。
```
