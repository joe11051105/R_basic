# 切換 R 的版本

因為有時候會安裝多個 R 的版本，但是 RStudio 通常系統會抓最新的版本當作目前的版本，但是有時需要換成舊的 R 版本？請參考以下程式碼(針對 Mac)。

### Step1 查看目前的版本

```
cd /Library/Frameworks/R.framework/Versions
ls -al

total 8
drwxrwxr-x  5 root  admin  170  8 10 17:02 .
drwxrwxr-x  8 root  admin  272  8 10 17:02 ..
drwxrwxr-x  6 root  admin  204  8 11 22:08 3.0
drwxrwxr-x  6 root  admin  204  8 11 22:04 3.1
lrwxr-xr-x  1 root  admin    3  8 10 17:02 Current -> 3.1
```

### Step 2刪除 Current

```
rm -rf Current
ls -al

total 0
drwxrwxr-x  4 root  admin  136  8 11 22:26 .
drwxrwxr-x  8 root  admin  272  8 10 17:02 ..
drwxrwxr-x  6 root  admin  204  8 11 22:08 3.0
drwxrwxr-x  6 root  admin  204  8 11 22:04 3.1
```

### Step 3 建立新的 Creent，並指向 3.0 版本

```
ln -s 3.0 Current
ls -al

total 8
drwxrwxr-x  5 root  admin  170  8 11 22:26 .
drwxrwxr-x  8 root  admin  272  8 10 17:02 ..
drwxrwxr-x  6 root  admin  204  8 11 22:08 3.0
drwxrwxr-x  6 root  admin  204  8 11 22:04 3.1
lrwxr-xr-x  1 joe   admin    3  8 11 22:26 Current -> 3.0
```

註：Windows & Linux 的部分可以參考 [RStudio](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) 官方文件

