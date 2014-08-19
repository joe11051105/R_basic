# 條件執行

### 常見的條件執行

以下介紹三種常見的條件執行。

+ if else
+ if else if else
+ switch

```r
# if A 判斷式
# A 判斷式為 True，會執行此區段程式碼。
# else
# A 判斷式為 False，會執行此區段程式碼。

> x <- 1

> if (x > 0) {
+   y <- 5
+ } else {
+   y <- 10
+ }

> if (x > 0) y <- 5 else y <- 10 # 單行的寫法。
> y
[1] 5

> y <- ifelse(x > 0, 5, 10) # 利用 ifelse(判斷式, True 給 5, False 給 10)。
> y
[1] 5

# if A 判斷式
# A 判斷式為 True，會執行此區段程式碼。
# else if B 判斷式
# B 判斷式為 True，會執行此區段程式碼。
# else
# A 與 B 判斷式都是 False，會執行此區段程式碼。

+   y <- 5
+ } else if (x > 2) {
+   y <- 10
+ } else {
+   y <- 3
+ }
> y
[1] 3

# switch(回傳數值代表執行第幾個程式片段, 程式片段 1, ..., 程式片段 N)
# switch(回傳名稱代表執行哪個名稱的程式片段, 程式名稱 A 片段, ..., 程式名稱 N 片段)

> switch(3, 10, 3 + 5, 3 / 3)
[1] 1
> switch(1, 10, 3 + 5, 3 / 3)
[1] 10
> switch(2, 10, 3 + 5, 3 / 3)
[1] 8

> switch("first", first = 1 + 1, second = 1 + 2, third = 1 + 3)
[1] 2
> switch("second", first = 1 + 1, second = 1 + 2, third = 1 + 3)
[1] 3
> switch("third", first = 1 + 1, second = 1 + 2, third = 1 + 3)
[1] 4
```
