# 資料框架

### 利用 data.frame 建立資料框架

資料框架類似資料表，常當作大量資料集，例如：匯入外部檔或讀取資料庫資料等。

```r
> name <- c("Joe", "Bob", "Vicky")
> age <- c("28", "26", "34")
> gender <- c("Male","Male","Female")
> data <- data.frame(name, age, gender)
> View(data) # 自動點選 data 變數就會開啟資料的畫面。
```

### 透過指標與名稱提取資料
資料框架的提取資料方法跟矩陣或陣列的都很類似。

```r
> data
       n  a      g
r1   Joe 28   Male
r2   Bob 26   Male
r3 Vicky 34 Female

> data[1,]
  name age gender
1  Joe  28   Male
> data[,1]
[1] Joe   Bob   Vicky
Levels: Bob Joe Vicky
> data[1, 1]
[1] Joe
Levels: Bob Joe Vicky

> data[,"name"]
[1] Joe   Bob   Vicky
Levels: Bob Joe Vicky
> data[1:2,"name"]
[1] Joe Bob
Levels: Bob Joe Vicky
> data$name[1:2]
[1] Joe Bob
Levels: Bob Joe Vicky
```

### 基本相關函數
+ header：取得資料框架前六比資料(預設是 6)。
+ names：修改或查詢 column 名稱。
+ colnames：設定 column 名稱。
+ row.names：修改或查詢 row 名稱。
+ rownames：設定 row 的名稱
+ summary：顯示資料基本資訊。

```r
> data
       n  a      g
r1   Joe 28   Male
r2   Bob 26   Male
r3 Vicky 34 Female

> head(data) # 因為筆數不夠多，所以全部都顯示。
       n  a      g
r1   Joe 28   Male
r2   Bob 26   Male
r3 Vicky 34 Female

> head(data, 1L) # 只顯示第一筆資料。
     n  a    g
r1 Joe 28 Male

> names(data)
[1] "name"   "age"    "gender"
> names(data) <- c("n", "a", "g")
> names(data)
[1] "n" "a" "g""
> colnames(data)
[1] "n" "a" "g"

> row.names(data)
[1] "1" "2" "3"
> row.names(data) <- c("r1", "r2", "r3")
> row.names(data)
[1] "r1" "r2" "r3"
> rownames(data)
[1] "r1" "r2" "r3"

> summary(data)
    name   age       gender
 Bob  :1   26:1   Female:1
 Joe  :1   28:1   Male  :2
 Vicky:1   34:1
```
