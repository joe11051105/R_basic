# 變數

R 在給予變數值時是利用「<-」並不是程式語言中常見的「=」，在 [Google's R Style Guide](http://google-styleguide.googlecode.com/svn/trunk/Rguide.xml#assignment) 與 [R 官方文件](http://stat.ethz.ch/R-manual/R-patched/library/base/html/assignOps.html) 都強調不該使用「=」，因為在某些狀況是會失效的。另外在 R 變數命名上，大小寫是有區別的，所以 x 與 X 其實是不同的變數。

```r
> x <- 1
> y <- 2
> x + y
[1] 3

> x1 <- x2 <- 1 # x1 與 x2 都是 1
> x1 + x2
[1] 2
```

R 的變數可以重複給予值，不會因為資料屬性的不同而發生錯誤，會因最後所給予的值為結果。所以程式碼複雜時，常常會因為一個變數重複給予不同的值而發生錯誤，這時可以用 exists 函數韓檢查。

```r
> x = 1
> x
[1] 1
> x = 1.3
> x
[1] 1.3
> x = 1 + 2i
> x
[1] 1+2i
> x = "test"
> x
[1] "test"
> x = FALSE
> x
[1] FALSE

> x = 10
> exists("x")
[1] TRUE
```

### NA 與 NULL

NA 代表是個空物件，已經有物件但是裡面沒東西，NULL 則是根本沒有任何東西，更詳細比較請參考 [R Bloggers R : NA vs. NULL](http://www.r-bloggers.com/r-na-vs-null/)
