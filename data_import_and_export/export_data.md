# 輸出資料

### 透過 write.table 輸出資料
以下利用 write.table 輸出 CSV 檔案。

```r
data <- iris # iris 是 R 內建的資料。
write.table(data, file = "test.CSV", sep = ",")
```

### 輸出 XML 檔案
跟輸入 XML 檔案一樣，是使用 XML package 來實做，但會需要利用到建立 tag 的函數。

```r
> data <- iris
> xml <- xmlTree()
> xml$addTag("document", close = FALSE) # 建立一個名為 document 的 tag。
> for (i in 1:nrow(data)) {
+   xml$addTag("row", close = FALSE) # 建立一個名為 row 的 tag。
+   for (j in names(data)) {
+     xml$addTag(j, data[i, j]) # j 為欄位名稱，所以是依序建立不同欄為名稱的 tag， 並賦予值與結束此 tag。
+   }
+   xml$closeTag() # 建立 tag 時，如果有下參數 close = FALSE 的話，記得要在結束 tag 地方下 closeTag()。
+ }
> xml$closeTag()
> saveXML(xml, "test.xml")
[1] "test.xml"
```

XML 檔案輸出結果。
```xml
<?xml version="1.0" encoding="UTF-8"?>
<document>
   <row>
      <Sepal.Length>5.1</Sepal.Length>
      <Sepal.Width>3.5</Sepal.Width>
      <Petal.Length>1.4</Petal.Length>
      <Petal.Width>0.2</Petal.Width>
      <Species>setosa</Species>
   </row>
   .
   .
   .
   .
</document>
```

### 輸出 RDA 檔案

利用 save 函數輸出 RDA 檔案。

```r
> data <- iris
> save(data, file="test.rda")
```
