### 下载安装Git

```
这里选择的是客户端安装版，地址：https://git-scm.com/download/win。
一直下一步即可，安装完成后，桌面右键如下：Git GUI Here（客户端） 和GIT Batch Here(终端)
```

---

### 本机生成公钥

#### 在Git终端依次输入：

```
1、cd ~/.ssh，显示 bash: cd: /c/Users/y/.ssh: No such file or directory则表示没有生成过公钥，如果不是则表示生成过公钥，可使用cat ~/.ssh/id_rsa.pub查看，也可在本地用户目录下的.ssh下查看。
2、生成公钥，命令如下：ssh-keygen。
3、查看公钥，命令如下：cat ~/.ssh/id_rsa.pub。
```

### 添加公钥

---

### 本地终端设置项：

#### 第一步：设置Git信息

```
git config --global user.name "花弧" 
git config --global user.email "null128@163.com"
```

#### 第二步，创建项目

```
mkdir hospital
cd hospital
git init
touch README.md
git add README.md
git commit -m "first commit"
git remote add origin https://gitee.com/null128/hospital.git//远程连接码云
```

#### 第三步，提交代码

```
git push origin master//需要输入的是码云注册邮箱跟密码
git pull origin master
```

----

### 分支

新建并切换到该分支，运行 `git checkout` 并加上 `-b` 参数：

```
$ git checkout -b develop
Switched to a new branch 'develop'
```

这相当于执行下面这两条命令：

```$ git branch iss53
$ git branch develop
$ git checkout develop
$ git merge master //更新master代码到分支
```

提交分支到远程服务器

```
$ git push origin develop
```

```json
查看本地分支：$ git branch
查看远程分支：$ git branch -r
创建本地分支：$ git branch [name] ----注意新分支创建后不会自动切换为当前分支
切换分支：$ git checkout [name]
创建新分支并立即切换到新分支：$ git checkout -b [name]
删除分支：$ git branch -d [name] ---- -d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项
合并分支：$ git merge [name] ----将名称为[name]的分支与当前分支合并
创建远程分支(本地分支push到远程)：$ git push origin [name]
```

-----

### Git pull 强制覆盖本地文件

```
git fetch --all  
git reset --hard origin/master 
git pull

备注：
git fetch 只是下载远程的库的内容，不做任何的合并 
git reset 把HEAD指向刚刚下载的最新的版本
```

### Git 查看当前所在分支

```
 git branch

前面带有星号（*）的分支就是当前所处的分支。如果再深究一下，也就是HEAD指针当指向的那个分支。
```

----

### 合并分支到master上

#### 假如我们现在在dev分支上，可以用下面命令查看当前分支

```
git branch
```

#### 刚开发完项目，执行了下列命令

```
git  add .
git  commit -m ‘dev'
git push -u origin dev
```

然后我们要把dev分支的代码合并到master分支上 该如何？

#### 首先切换到master分支上

```
git  checkout master
```

如果是多人开发的话 需要把远程master上的代码pull下来

```
git pull origin master
```

如果是自己一个开发就没有必要了，为了保险期间还是pull
然后我们把dev分支的代码合并到master上

```
git  merge dev
```

然后查看状态

```
git status
```

#### 执行下面命令即可

```
git push origin master
```

