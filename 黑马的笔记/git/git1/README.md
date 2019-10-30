# Git

## 什么是 Git?

- Git 是一款源代码管理工具(版本控制工具)
  - 分布式的版本控制工具
  - 我们写的代码需要使用 Git 进行管理。
- 源代码有必要管理起吗？
- 1.0
- 2.0 //
- svn,vss,vcs.... git
- 有必要，因为人工的去处理不同的版本，做相应备份会很麻烦。
- Git 是 linux 之父当年为了维护 linux---linus 之前也是手动维护合并把文件发给 Linus
- linus 自己写了一个版本管理的工具(Git)

## Git 安装

## 初始化 Git 仓储/(仓库)

- 这个仓库会存放，git 对我们项目代码进行备份的文件
- 在项目目录右键打开 git bash
- 命令: `git init` -> 创建仓库

## 自报家门

- 就是在 git 中设置当前使用的用户是谁
- 每一次备份都会把当前备份者的信息存储起来
- 命令:
  - 配置用户名:`git config --global user.name "xiaoming"`
  - 配置邮箱: `git config --global user.email "xm@sina.com"`

```git
git init   // 初始化
git config --global user.name "myname"    // 全局配置,配置身份
git config --global user.email "myemail.qq.com"  // 邮箱

git add --all / git add ./file
git commit -m 'message'


```
![Ke8nte.png](https://s2.ax1x.com/2019/10/18/Ke8nte.png)
## 查看配置
- `git config --list`  显示当前 git 的配置
- `git config -e [,--global]`   : -e 是编辑， --global 是配置全局的 配置。

## 把大象放到冰箱要几步

1) 选择要存储的文件 add
2) 提交 commit -m

## 把代码存储到.git 仓储中

- 1.把代码放到仓储的门口
  - `git add ./readme.md` 所指定的文件放到大门口
  - `git add ./` 把==所有==的修改的文件添加到大门口
- 2.把仓储门口的代码放到里面的房间中去
  - `git commit -m "这是对这次添加的东西的说明"`
  - -m => --massage 消息,注释.

## 可以一次性把我们修改的代码放到房间里(版本库)

- `git commit --all -m "一些说明"`
  - --all 表示是把所有==修改==的文件提交到版本库

## 查看当前的状态

- 可以用来查看当前代码有没有被放到仓储中去
- 命令: `git status`
  - 文件( 绿色 标志 )出来, 就是 选中 git 了(成为 staged 暂存区)的, 但是还没有提交.
  - working directory clean . 工作目录干净的, 就是都提交了的.
  - 红色标志 文件 就是 没有选中, 也没有提交.

## git 中的忽略文件

- .gitignore,在这个文件中可以设置要被忽略的文件或者目录。
- 被忽略的文件不会被提交仓储里去.
- 在.gitignore 中可以书写要被忽略的文件的路径，以/开头，
  一行写一个路径，这些路径所对应的文件都会被忽略，
  不会被提交到仓储中
  - 写法
    - `/.idea` 会忽略.idea 文件
    - `/js` 会忽略 js 目录里的所有文件
    - `/js/*.js` 会忽略 js 目录下所有 js 文件

## 查看日志

- `git log` 查看历史提交的日志
- `git log --oneline` 可以看到简洁版的日志

## 回退到指定的版本

- `git reset --hard Head~0`
  - 表示回退到上一次代码提交时的状态
- `git reset --hard Head~1`

  - 表示回退到上上次代码提交时的状态

- `git reset --hard [版本号]` 就是前面的那个唯一标识符

  - 可以通过版本号精确的回退到某一次提交时的状态

- `git reflog`
  - 可以看到每一次切换版本的记录:可以看到所有提交的版本号

## 分支

- 默认是有一个主分支 master

### 创建分支

- `git branch dev`
- `git branch` `查看分支`
  - 创建了一个 dev 分支
  - 在刚创建时 dev 分支里的东西和 master 分支里的东西是一样的

### 切换分支

- `git checkout dev`
  - 切换到指定的分支,这里的切换到名为 dev 的分支
    `git branch` 可以查看当前有哪些分支

### 合并分支

- `git merge dev`
  - 合并分支内容,把当前分支与指定的分支(dev),进行合并
  - 当前分支指的是`git branch`命令输出的前面有\*号的分支
- 合并时如果有冲突，需要手动去处理，处理后还需要再提交一次.

### GitHub

- https://github.com
- 不是 git,只是一个网站
- 只不过这个网站提供了允许别通过 git 上传代码的功能

### 提交代码到 github(当作 git 服务器来用)

- https://github.com/litaoAurora/js--.git
- 需要 github 的用户名和用户密码。
- liaurora4@gmail.com
- 625716987@qq.com
- name : litaoAurira
- pwd: Aurora625716987

- `git push [地址](github项目的地址) master`

* 示例: `git push https://github.com/huoqishi/test112.git master master`
* 会把当前分支的内容上传到远程的 master 分支上

- 拿到之前提交到 github 上的文件
- 还得先 init 舒适化仓库。
- `git pull [地址] master`
- 还能到的 git log 的历史版本

* 示例: `git pull https://github.com/huoqishi/test112.git master`
* 会把远程分支的数据得到:(_注意本地-要初始一个仓储!_)

- `chone and download` 在 github 上
- `git clone [地址]`

  - 会覆盖原来的。

- ssh 提交
  - 生成公钥和私钥。
  - ssh-keygen -t rsa - C '625716987@qq.com'
  - 公钥
  - 私钥

* 会得到远程仓储相同的数据,如果多次执行会覆盖本地内容。

# my-note

### - 与 --

`-` 是短选项 `short option` `unix` 风格

`--` 是长选项 `long option` `gnu` 风格

==`通常以短选项都 会有一个长选项与之对应` 短选项与长选项本质是一样的 如==

- `-a => --all`

- `-v => --version`

- `-f => --file`

###### 参数 用空格隔开 空格 等于 `=`

- `-f book.html => -f=bookhtml`

一条命令 = > 命令 + 选项 + 参数

## Git options

[file:///C:/Program%20Files/Git/mingw64/share/doc/git-doc/git-commit.html](file:///C:/Program Files/Git/mingw64/share/doc/git-doc/git-commit.html)

本地的 Git help 文件

- -a
  - --all
- -p
  - --patch 补丁
- -d
  - --delete

git remote add origin http: …  **链接远程**
git push -u ..      **上传**



# 新的

> 流程是 ： 每次提交的代码都要是  pull 一次 github 的最新代码来 保存，合并。 
>
> 接下来才是 提交。  先 pull 在 push .



- 公司的是 gitlab

官网 : `https://git-scm.com/download/linux`

`[https://www.git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git](https://www.git-scm.com/book/zh/v2/起步-安装-Git)`

## 安装

```txt

sudo yum install git  // yum  liunx安装
sudo apt-get install git   // apt-get
s

```



## 配置  `config` 

> 控制git  外观和行为的配置变量。 

1 三个配置管理包 : 

  `/etc/gitconfig`     **—system**

 `~/.gitconfig`     **用户    —global**



用户信息 ： (不可更改)

```txt

git config --global user.name "John Dne" // 配置名字
git config --global user.email "johd.com"  // 

git confing --list   // 检查配置信息

```

>  `--global` 选项，那么该命令只需要运行一次，因为之后无论你在该系统上做任何事情， Git 都会使用那些信息

### 检查配置信息

`git confing --list`   // 检查配置信息



