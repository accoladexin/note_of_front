# 1. Git的配置与安装



## 1.1 git的安装

git下载地址：https://git-scm.com/downloads 下载对应系统的版本，后面直接全选安装就可以了。


## 1.2  配置Git用户信息

首相配置用户的姓名的邮箱

```git
git config --global user.name "xinxindeng"
git config --global user.email "1027842619@qq.com"
```

注意:如果使用了 --global选项, 那么该命令只需要运行一次,即可永久生效.

通过`git config --global user.name` 和` git config --global user.email`配置的用户名和邮箱地址，会被写 入到`C:/Users/`用户名文件夹`/.gitconfig`文件中。这个文件是Git 的全局配置文件，配置一次即可永久生效。
可以使用记事本打开此文件，从而查看自己曾经对Git 做了哪些全局性的配置。

![image-20211028222952096](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211028222952096.png)

## 1.3 检查配置信息

查看全局配置文件

```git
git config --list --global
```

除了使用记事本查看全局的配置信息之外，还可以运行如下的终端命令，快速的查看Git 的全局配置信息

```git
git config user.name
git config user.email
```

![image-20211028223151291](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211028223151291.png)

## 1.4 获取帮助信息

可以使用 `git help <verb> `命令，无需联网即可在浏览器中打开帮助手册，例如：

```
git help config
```

如果不想查看完整的手册，那么可以用-h 选项获得更简明的“help”输出：

```
git config -h
```

# 2. Git的基本操作

## 2.1 获取 Git 仓库的两种方式

① 将尚未进行版本控制的本地目录转换为Git 仓库 

② 从其它服务器克隆一个已存在的Git 仓库

以上两种方式都能够在自己的电脑上得到一个可用的 Git 仓库

## 2.2 在现有目录中初始化仓库

如果自己有一个尚未进行版本控制的项目目录，想要用Git 来控制它，需要执行如下两个步骤：

 ① 在项目目录中，通过鼠标右键打开`“Git Bash”`

 ② 执行`git init `命令将当前的目录转化为Git 仓库

git init 命令会创建一个名为`.git `的隐藏目录，这个.git 目录就是当前项目的Git 仓库，里面包含了初始的必要 文件，这些文件是Git 仓库的必要组成部分。这个文件一定不要删除,删了仓库就没了.

```Git
git init
```

## 2.3 工作区中文件的 4 种状

![image-20211029103836869](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029103836869.png)

Git 操作的终极结果：让工作区中的文件都处于“未修改”的状态.

## 2.4 检查文件状态

```
 git status 
```

![image-20211029104213883](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029104213883.png)

上面表示未被跟踪文件.

还有另外两种查询方法:

```
git status -s
git status -short
```

上面两种方式等价

![image-20211029104531398](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029104531398.png)

红色的??表示为跟踪文件

## 2.5 跟踪新的文件

使用命令 `git add 文件名`开始跟踪一个文件。

```
 git add index.css
```

使用`git add .`将所有文件添加到跟踪文件.

```
 git add .
```

![image-20211029104930792](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029104930792.png)

绿色表示都没跟踪了.

## 2.6 提交更新

暂存区中有一个index.html 文件等待被提交到Git 仓库中进行保存。可以执行` git commit` 命令进行提交, 其中-m 选项后面是本次的提交消息，用来对提交的内容做进一步的描述：

```
git commit -m "新建了三个文件"
```

![image-20211029105414314](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029105414314.png)

![image-20211029110109032](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029110109032.png)

目前，index.html 文件已经被Git 跟踪，并且工作区和Git 仓库中的index.html 文件内容保持一致。当我们 修改了工作区中index.html 的内容之后，再次运行git status 和 git status -s 命令，会看到如下的内容：

![image-20211029110409431](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029110409431.png)

注意：修改过的、没有放入暂存区的文件前面有红色的M 标记。

## 2.7 暂存已修改的文件

目前，工作区中的index.html 文件已被修改，如果要暂存这次修改，需要再次运行git add 命令，这个命令 是个多功能的命令，主要有如下3 个功效： 

① 可以用它开始跟踪新文件 

② 把已跟踪的、且已修改的文件放到暂存区

 ③ 把有冲突的文件标记为已解决状态

![image-20211029110736986](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029110736986.png)

绿色表示文件已经修改而且放入了暂存区.

## 2.8 提交已暂存的文件



再次运行 git commit -m "提交消息" 命令，即可将暂存区中记录的index.html的快照，提交到Git 仓库中进 行保存

![image-20211029111122031](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029111122031.png) 

![image-20211029111132552](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029111132552.png)

## 2.9 撤销对文件的修改

撤销对文件的修改指的是：把对工作区中对应文件的修改，还原成Git 仓库中所保存的版本。 操作的结果：所有的修改会丢失，且无法恢复！危险性比较高，请慎重操作！

![image-20211029111237322](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029111237322.png)

```
git checkout --index.html
```

## 2.10 取消暂存文件

如果需要从暂存区中移除对应的文件，可以使用如下的命令：

```
git reset HEAD 移除文件的名称
```

## 2.11 跳过使用的暂存区域

Git 标准的工作流程是工作区→ 暂存区 → Git 仓库，但有时候这么做略显繁琐，此时可以跳过暂存区，直接将 工作区中的修改提交到Git 仓库，这时候Git 工作的流程简化为了工作区→ Git 仓库。 Git 提供了一个跳过使用暂存区域的方式，只要在提交的时候，给git commit 加上-a 选项，Git 就会自动把 所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤：

```
git commit -a -m "描述信息"
```

##  2.12 移除文件

从 Git 仓库中移除文件的方式有两种：

 ① 从 Git 仓库和工作区中同时移除对应的文件

 ② 只从Git 仓库中移除指定的文件，但保留工作区中对应的文件

```
# 从Git仓库和工作区同事移除文件 index.js
git rm -f index.js
# 只从仓库中移除文件 index.css
git rm  --cached index.css
```

