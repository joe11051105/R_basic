# 匯入資料


### 透過 read.table 匯入資料。

read.table 可以讀取大多數的 ASCII 資料，以下先以 CSV 檔為代表，因為是目前最普遍見到的匯入資料格式。

```r
> data <- read.table("Desktop/data.csv", header = TRUE, sep = ",") # 檔案路徑是相對於目前的工作目錄，header 是指資料是否有包含欄位名稱，sep 是指資料的分隔符號。

> data <- read.table("Desktop/data.csv", header = TRUE, sep = ",", col.names = c("時間", "新聞標題")) # col.names 設定 column 欄位名稱。

> data <- read.table("Desktop/data.csv", header = FALSE, sep = ",", skip = 10) # skip 是指跳過前 X 筆資料，這個部份要注意，要跳過資料，column 欄位就不可以出現在資料裡，因為它也被算在要 skip 部份。

> data <- read.table("Desktop/data.csv", header = TUE, sep = ",", encoding = "UTF-8") # encoding 是指定檔案的文字編碼

> data <- read.table("Desktop/data.csv", header = TRUE, sep = ",", na.strings = NA) # na.strings 指定發生 NA 要用什麼符號代替。
```

### 文字編碼問題

匯入 CSV 檔的時候會碰到一種比較特別的問題，就是作業系統編碼不同的問題，Windows 的中文編碼是 big5，而 Linux / Mac 都是 UTF-8，所以在 Linux / Mac 匯入來自於 Windows CSV 檔常常會發生亂碼，那該如何解決此問題，本人的做法是將資料讀進來轉成 UTF-8，在輸出一份 CSV 檔，以下先以一個 CSV 檔為主，加以調整修改就可以改成一次跑一個資料夾下的所有 CSV 檔。

```r
> data <- readLines("Desktop/A_lvr_land_A.CSV", encoding="big5") # 讀取實價登入資料，是一行一行讀取進來。
> data <- iconv(data, "big5", "utf8") 將資料轉成 UTF-8。

> column_count <- length(strsplit(data[1], ",")[[1]])
row_count <- length(data) # 計算 column 與 count 個數。

> fix_data <- matrix(NA, nrow = row_count, ncol = column_count) # 建立一個空的 NA 矩陣，維度來自於 row_count 與 column_count。

> for(row in 1:row_count) {
+     for(col in 1:column_count) {
+         fix_data[row,col] <- strsplit(data[row], ",")[[1]][col] # 執行 for loop 將資料塞入 fix_data。
+     }
+ }

> write.table(fix_data[2:row_count,], file = "fix_A_lvr_land_A.CSV", sep = ",", col.names = fix_data[1,]) # 將資料輸出，輸出注意一點，因為第一 row 是欄位名稱，所以記得指標要從 2 開始，指標 1 的部分要放到 col.names。
```
### 讀取 XML 檔案。

這邊順便也介紹讀取 XML 方法，是因為讀取 XML 檔案比較不會發生上述的編碼問題，所以如果兩者都會的話，以後有提供 CSV 與 XML 檔案時，就可以選 XML 檔案以免製造自己的麻煩。


```r
> library(XML) # 要先安裝 XML package 再載入。
> data <- xmlToDataFrame("Desktop/A_lvr_land_A.XML")
```

### 匯入 RDA 檔案

匯入 RDA 檔案有以下兩種方式。

+ 在工作目錄直接點選 RDA 檔案，選擇匯入即可。
+ 在 console 下 load(檔案名稱)。
