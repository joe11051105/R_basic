### 因子

### 利用 factor 建立因子

因子有點像經過分級之後的向量，因子大多可以用在統計上的迴歸分西與實際設計等。

```r
> x <- c(1, 2, 4, 3, 1, 2, 3, 4,1)
> factor(x)
[1] 1 2 4 3 1 2 3 4 1
Levels: 1 2 3 4

> factor(x, labels = c("一", "二", "三", "四")) # 可自訂 Level 的名稱。
[1] 一 二 四 三 一 二 三 四 一
Levels: 一 二 三 四

> factor(x, ordered = TRUE) # ordered 代表可做排序
[1] 1 2 4 3 1 2 3 4 1
Levels: 1 < 2 < 3 < 4

> factor(c(1, 2, 1, NA, 2), exclude = NA) # 可利用 exclude 排除特定資料。
[1] 1    2    1    <NA> 2
Levels: 1 2

> factor(c(1, 2, 1, NA, 2), exclude = 2)
[1] 1    <NA> 1    <NA> <NA>
Levels: 1 <NA>

> factor(c(1, 2, 1, NA, 2), exclude = NULL) # 不排除任何資料。
[1] 1    2    1    <NA> 2
```

### 透過指標提取資料

```r
> x[1] # [] 與 [[]] 結果一致，因為因子只有值沒有其他相關資料。
[1] 1
> x[[1]]
[1] 1

> x[1:2] # 指標可以使用向量。
[1] 1 2

> x[c(1, 3, 5)]
[1] 1 4 1
```


### 基本相關函數

+ is.factor：判斷是否為因子。
+ as.factor：將變數轉為因子。
+ is.ordered：判斷是否為排序過的因子。
+ as.ordered：將因子排序。
+ which：找出符合條件的指標。

```r
> x <- c(1, 2, 4, 3, 1, 2, 3, 4,1)

> as.factor(x)
[1] 1 2 4 3 1 2 3 4 1
Levels: 1 2 3 4
> is.factor(x)
[1] FALSE
> is.factor(as.factor(x))
[1] TRUE

> is.ordered(factor(x, ordered = TRUE))
[1] TRUE
> is.ordered(factor(x, ordered = FALSE))
[1] FALSE
> as.ordered(factor(x))
[1] 1 2 4 3 1 2 3 4 1
Levels: 1 < 2 < 3 < 4

> which(x == 1) # 找出 x 等於 1 的指標
[1] 1 5 9
```
