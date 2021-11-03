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

红色的??表示未跟踪文件

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

![image-20211029112314029](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029112314029.png)

![image-20211029112331318](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029112331318.png)

index.js都被删除了,但是index.css在工作区里面还有.

## 2.13忽略文件

一般我们总会有些文件无需纳入Git 的管理，也不希望它们总出现在未跟踪文件列表。在这种情况下，我们可 以创建一个名为.gitignore的配置文件，列出要忽略的文件的匹配模式。 文件.gitignore 的格式规范如下：

 ① 以 # 开头的是注释

 ② 以 / 结尾的是目录

 ③ 以 / 开头防止递归 

④ 以 ! 开头表示取反 

⑤ 可以使用 glob 模式进行文件和文件夹的匹配（glob 指简化了的正则表达式）

glob模式

所谓的glob 模式是指简化了的正则表达式：

 ① 星号 * 匹配零个或多个任意字符

 ② [abc] 匹配任何一个列在方括号中的字符（此案例匹配一个a 或匹配一个b 或匹配一个c）

 ③ 问号 ? 只匹配一个任意字符

 ④ 在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如[0-9] 表示匹配 所有0 到 9 的数字） 

⑤ 两个星号 ** 表示匹配任意中间目录（比如a/**/z 可以匹配 a/z 、 a/b/z 或 a/b/c/z 等）

![image-20211029124849853](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029124849853.png)

## 2.14 查看提交历史

```
git log 
git log -2 #查看最新提交历史
git log -2 --pretty=online #在一行展示最近两条提交的历史信息

git log -2 --pretty=format:"%h | %an | %ar | %s"
```

![image-20211029125701722](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029125701722.png)

## 2.15 回退到指定的版本

```Git
git log --pretty=oneline
git reset --hard <CommitID>

git reflog --pretty=oneline
git reset --hard <CommitID>
```

![image-20211029130341610](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029130341610.png)

![image-20211029130326567](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029130326567.png)

## 2.16 小结

① 初始化 Git 仓库的命令 ` git init`

 ② 查看文件状态的命令 `git status`或` git status -s `

③ 一次性将文件加入暂存区的命令` git add `. 

④ 将暂存区的文件提交到Git 仓库的命令 ` git commit -m `提交消息"

# 3. Github使用与配置

网址`https://github.com/`

## 3.1新建空白远程仓库

直接上老师的图

![image-20211029154415384](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029154415384.png)

建立成功:

![image-20211029154445515](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029154445515.png)

## 3.2远程仓库的两种方式

Github 上的远程仓库，有两种访问方式，分别是HTTPS和 SSH。它们的区别是： 

① HTTPS：零配置；但是每次访问仓库时，需要重复输入 Github 的账号和密码才能访问成功

 ② SSH：需要进行额外的配置；但是配置成功后，每次访问仓库时，不需重复输入Github 的账号和密码

注意：在实际开发中，推荐使用SSH 的方式访问远程仓库。

### 3.2.1 HTTPS将本地仓传到Github

![image-20211029154624072](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029154624072.png)

### 3.2.2 SSH远程链接

SSH key 的作用：实现本地仓库和 Github 之间免登录的加密数据传输。 

SSH key 的好处：免登录身份认证、数据加密传输。 

SSH key 由两部分组成，分别是：

 ① id_rsa（私钥文件，存放于客户端的电脑中即可）

 ② id_rsa.pub（公钥文件，需要配置到 Github 中）

#### 生成SSH Key

  ① 打开Git Bash

 ② 粘贴如下的命令，并将`your_email@example.com `替换为注册` Github` 账号时填写的邮箱：

 ```
 ssh-keygen -t rsa -b 4096 -C "accoladexin@example.com" 
 ```

③ 连续敲击 3 次回车，即可在C:\Users\用户名文件夹\.ssh目录中生成id_rsa和 id_rsa.pub 两个文件

![image-20211029155430171](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029155430171.png)

#### 配置SSH

位置`C:\Users\Administrator\.ssh`

① 使用记事本打开id_rsa.pub文件，复制里面的文本内容 

![image-20211029155614658](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029155614658.png)

② 在浏览器中登录Github，点击头像-> Settings-> SSH and GPG Keys -> New SSH key 

![image-20211029155832933](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029155832933.png)

![image-20211029160146252](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029160146252.png)

③ 将 id_rsa.pub 文件中的内容，粘贴到Key 对应的文本框中 

④ 在 Title 文本框中任意填写一个名称，来标识这个Key 从何而

####  检测是SSH是否配置成功

打开Git Bash，输入如下的命令并回车执行：

```
ssh -T git@github.com
```

![image-20211029160634226](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029160634226.png)

上述的命令执行成功后，可能会看到如下的提示消息：

![image-20211029160713860](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029160713860.png)

输入yes 之后，如果能看到类似于下面的提示消息，证明SSH key 已经配置成功了：

![image-20211029160729345](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029160729345.png)

全图:

![image-20211029160823378](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029160823378.png)

## 3.3 基于 SSH 将本地仓库上传到 Github

![image-20211029160907367](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029160907367.png)

只管复制就好了

这个是首次上传是这样的

## 3.4 将远程仓库克隆到本地

打开Git Bash，输入如下的命令并回车执行：

```
git clone 远程的地址
```

![image-20211029161817912](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211029161817912.png)

# 4. Git分支

## 4.1本地操作

### 4.1.1查看分支列表

```
git branch
```

![image-20211103195907323](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103195907323.png)

注意：分支名字前面的* 号表示当前所处的分支

### 4.1.2 创建新分支

```
git branch 分支名称
```

![image-20211103200056084](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103200056084.png)

### 4.1.3 切换分支

```
git checkout 分支名称
```

![image-20211103200230078](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103200230078.png)

![image-20211103200343474](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103200343474.png)

### 4.1.4分支的快速创建和切换

使用如下的命令，可以创建指定名称的新分支，并立即切换到新分支上：

```
# -b 表示创建一个新的分支
# checkout 表示切换
git checkout -b 分支名称
```

![image-20211103200825550](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103200825550.png)

###  4.1.5合并分支

功能分支的代码开发测试完毕之后，可以使用如下的命令，将完成后的代码合并到main 主分支上：

```
# 先切换到main上去
git checkout main
#在合并
git merge 分支名称
```

![image-20211103201236499](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103201236499.png)

![image-20211103201247844](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103201247844.png)

合并分支时的注意点： 假设要把C 分支的代码合并到A 分支， 则必须先切换到A 分支上，再运行git merge 命令，来合并C 分支！

### 4.1.6 删除分支

当把功能分支的代码合并到main主分支上以后，就可以使用如下的命令，删除对应的功能分支：

```
git branch -d 分支名称
```

![image-20211103202709566](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103202709566.png)

### 4.1.7遇到冲突时的分支合

如果在两个不同的分支中，对同一个文件进行了不同的修改，Git 就没法干净的合并它们。此时，我们需要打开 这些包含冲突的文件然后手动解决冲突。

![image-20211103202801721](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103202801721.png)

## 4.2远程分支操作

### 4.2.1将本地分支推送到远程仓库

如果是第一次将本地分支推送到远程仓库，需要运行如下的命令：(可能现在更新了)

![image-20211103202908609](git%E4%B8%8EGithub%E4%BD%BF%E7%94%A8.assets/image-20211103202908609.png)

注意：第一次推送分支需要带-u 参数，此后可以直接使用git push 推送代码到远程分支。

### 4.2.3查看远程仓库中所有的分支列表

```
git remote show 远程仓库名字
```



