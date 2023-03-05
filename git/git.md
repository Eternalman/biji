#### 克隆远程仓库

`git clone 仓库网址` 

会出现一个仓库名称的文件



#### 加载到版本库的缓冲区

`git status`  查看仓库当前的状态，显示有变更的文件。

`git add  [被修改文件]`



#### 将改动提交到本地仓库

`git commit -m "修改后说明"`

 

#### 推送到远程仓库

查看克隆和推送仓库的地址

`git remote -v`

`git push` 推送到远程仓库



本地仓库同步远程库

```
git pull
```

git pull origin master --allow-unrelated-histories