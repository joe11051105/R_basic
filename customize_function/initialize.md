# 建立 .First 與 .Last 函數

R 可以利用 .First 與 .Last 函數，建立 R 環境 開始與結束時會自動執行的函數。

+ 建立 .Rprofile 檔案
+ 建立 .First 與.Last 函數

```
touch ~/.Rprofile

open -a Textedit ~/.Rprofile
```

.Rprofile 檔案內容
```
.First = function()
{
  library(ggplot2) # 開啓 RStudio 時會自動載入ggplot2package
}

.Last = function()
{

}
```

註：以上是在 Mac 環境下操作，但不同環境應該大同小異。
