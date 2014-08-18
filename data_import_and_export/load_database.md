# 讀取資料庫的資料

### 讀取資料庫的資料
利用 DBI、gWidgets、RMySQL 與 dbConnect 等 package 讀取資料庫資料。

```r
> library(DBI)
> library(gWidgets)
> library(RMySQL)
> library(dbConnect)
> con <- dbConnect(MySQL(), dbname = "house_development", username="root", password="123456")
>
> dbSendQuery(con,"SET NAMES utf8") #需設定 UTF-8，不然中文會亂碼。
<MySQLResult:(94576,0,0)>
> dbClearResult(dbListResults(con)[[1]])
[1] TRUE
>
> dbGetQuery(con,"show variables like 'character_set_%'")
Variable_name Value
character_set_client utf8
character_set_connection utf8
character_set_database utf8
character_set_filesystem binary
character_set_results utf8
character_set_server utf8
character_set_system utf8
character_sets_dir /usr/local/Cellar/mysql/5.6.12/share/mysql/charsets/

data = dbGetQuery(con, "select * from raws") # 這邊是使用 Mysql。
```

註：如果資料庫不太熟，卻又想學習基本的語法的話，推薦 [新SQL 基礎講座 <增訂第二版>](http://www.books.com.tw/products/0010396522)，此本的好處是記載不同資料庫的語法且前顯易懂。
