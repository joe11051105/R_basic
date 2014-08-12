# 資料屬性
R 的基本資料屬性包含以下五種，可用 class 函數判斷資料屬性

+ character：文字字串，用 "" 包起來，ex："test"
+ numeric：實數
+ integer：整數
+ complex：複數
+ logical：True 或 False

```r
> class("test")
[1] "character"

> class(10.10)
[1] "numeric"

> class(10)
[1] "numeric"

> class(as.integer(3)) # 因為 R 計算上是都是以雙倍精確度來計算，所以必須指定為 integer，不然都會被當成 numeric 看待。
[1] "integer"

> class(as.integer(3.1)) # as.integer 可以將不是整數的數值變成整數
[1] "integer"

> class(as.integer(T)) # as.integer(T) = 1
[1] "integer"

> class(as.integer(F)) # as.integer(T) = 0
[1] "integer"

> class(2+2i)
[1] "complex"

> class(TRUE) # 注意都要大寫，不可寫 True，但可以簡化成 T
[1] "logical"

> class(T)
[1] "logical"
```
註：
+ as.integer 切記不可以傳 character 進去，因為會產生 NA，如果傳 complex 進去，則會將虛數的部份則會自動捨棄。
+ 可以用 is.integer(x) 判斷是否為整數。
+ complex 也有跟 integer 類似的函數，as.complex 與 is.complex。
+ logical 也有跟 integer 類似的函數，as.logical 與 is.logical

|  | character | numeric | integer | complex | logical |
| -- | :--: | :--: | :--: | :--: | :--: |
| as.integer | X | Ｏ | Ｏ | Ｏ | Ｏ |
| is.integer | F | F | T | F | F |
