### 安裝載入 package

### 安裝 package

安裝 package 有以下兩種方式：

+ 透過右下角 Packages -> Install Packages 安裝套件
+ 在 console 輸入指令安裝

```r
> install.packages("ggplot2") # 下載 ggplot2 套件
```

### 載入 package

載入 package 有以下料、兩種方式：

+ 透過右下角 Package，將要載入的 package 打勾即可。
+ 在 console 輸入指令載入

```r
> library(ggplot2) # ggplot2 一個畫圖套件。

> require(ggplot2) # library 與 require 都是載入 package，但是最大的差別在於，library 如果是載入的 package 不存在，是會發生 error 程式停止，但是 require 卻不會。
```

不過以上下載的套件是指發佈在 CRAN 上的，但如果沒有發佈在 CRAN，而是發佈在 Github 上該怎麼辦，可以利用 devtools package 實作此部份。

```r
> install.packages("devtools")
> require(devtools)
> install_github("rpensoft", "ropensci") # package 名稱為 rpensoft，repository 名稱為 ropensci，對應到的 github 網址為 https://github.com/ropensci/rpensoft。

```
