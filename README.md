# q_git_use
## 基本操作
初始化仓库
`git init`

查看仓库当前分支的状态
`git status `

将当前分支的所有改变添加到暂存区
`git add .`  

将将当前分支的的暂存区提交
`git commit -m "init"`


查看所有分支
`git branch`


切换分支当分支不存在时先创建一个分支dev，当分支存在时会提示
分支已存在，切不会切换
`git checkout -b dev`

切换分支dev
`git checkout  dev`

合并分支，要合并一个分支先切换的另一个分支如main，然后合并
`git merge dev`

删除本地分支
`git branch -d dev`


创建忽略文件 自文件制定的文件或目录将不会做为仓库的管理内容
`touch .gitignore`


# `.gitignore` 不生效操作
1. 清除本地当前的Git缓存
`git rm -r --cached .`
2. 应用.gitignore等本地配置文件重新建立Git索引
`git add .`

3. 提交当前Git版本并备注说明
`git commit -m 'update .gitignore'`

# 冲突的的例子和解决
冲突的产生，在不同分支或者不同的用户对同一个文件进行编辑提交，且编辑前没有合并另一个分支的提交更新直接编辑提交后而合并

## 制造冲突
1 首先我们在`dev分支`对`index.md`文件添加如下内容：
```
初始内容

在dev分支添加的新内容：hello dev

```
2 将`dev分支`的改变提交,然后切换的`main分支`
在`main分支`中对`index.md`文件添加如下内容：
```
初始内容
在main分支添加的新内容：hello main

```
3 提交`main分支`的改变，然后合并`dev分支`的提交，冲突产生了,产生的的内容如下：
```

初始内容
<<<<<<< HEAD
在main分支添加的新内容：hello main
=======

在dev分支添加的新内容：hello dev
>>>>>>> dev

```
## 冲突的解释和说明
从以上内容中 `<<<<<<< HEAD` 和 `=======` 之间的内容是当前分支添加的新内容
而`=======`和`>>>>>>> dev`之间的内容是另一个分支即要合并的对应分支，这里是`dev 分支`
新添加的内容。记住`<<<<<<< HEAD`永远指向当前分支

## 冲突的解决
如何取舍呢?可以根据实际情况保留其中一个分支的内容或者都保留。然后删除掉 `<<<<<<< HEAD` 和 `=======`以及`>>>>>>> dev`这些字符，最后提交，我们这里就都保留吧。

最后提交解决完冲突的更新后，最好将其合并到我们之前合并的分支，这里就是将`main 分支`的冲突解决更新合并到`dev 分支`，这样两个分支就保持一致了


git status 的输出`Unmerged`冲突文件列表
Unmerged paths:下面列出的就是全部冲突文件，挨个解决即可


# 远程仓库的一些操作

查看远程仓库地址
`git remote -v`


推送指定分支
`git push --set-upstream origin dev`

删除远程分支
`git push origin -d dev`

clone 远程仓库
`git clone https://github.com/HeHuiqi/q_git_use.git`

拉取远程dev分支

`git checkout -b dev origin/dev `

