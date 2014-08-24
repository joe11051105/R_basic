# 資料變形

在第三章常提到 as 開頭的函數，例如：as.vector、as.array、as.matric、as.data.frame 等，其實就是資料變形函數的一種，以下介紹其他常用到的資料變形函數。

+ stack 與 unstack 函數
+ reshape 函數

```r
> data <- iris # 使用 R 內建的資料。

> stack_data <- stack(data) # stack 函數將各行資料排成一直行，unstack 則是還原成未 stack 之前形態。

> library("longitudinalData")
> data <- artificialJointLongData # 此種資料稱作為縱向資料(Longitudinal Data)，通常是單一物體重複測量值所產生的資料，記錄方式可以用長型資料(long format)或寬型資料(wide format)。

> data_long = reshape(data, direction="long", varying = list(c("v0", "v1", "v2", "v3", "v4", "v5", "v6", "v7", "v8", "v9", "v10"), c("w0", "w1", "w2", "w3", "w4", "w5", "w6", "w7", "w8", "w9", "w10"), c("x0", "x1", "x2", "x3", "x4", "x5", "x6", "x7", "x8", "x9", "x10")), v.names = c("v", "w", "x"), idvar = "id") # 利用 reshape 函數將資料從 wide 轉成 long

> data_wide = reshape(data_long, direction="wide",v.names = c("v", "w", "x"), idvar = "id") # 利用 reshape 函數將資料從 long 轉成 wide
```

解釋以上 reshape 函數一些參數的用意。

+ direction：資料要轉成哪種類型，long 或 wide。
+ varying：用於 wide 轉 long 時，哪些欄位要變成一個欄位的長期觀察資料，例如 v0 ~ v1 要變成 v，w0 ~ w10 變成 w，x0 ~ x10 變成 x。
+ v.names：對於 wide 轉 long 時，當作是 long 資料的欄位，對於 long 轉 wide，哪些欄位要變成多個欄位觀察值。
+ idvar：非重複性觀察資料，多半是可以分辨觀察物體的變數，，例如：id、名稱等。
