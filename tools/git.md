

## 安装git的方法
Mac OS系统：通过homebrew工具安装
```
brew install git
```
## 配置Git
git必须先配置再使用。`Git config`命令用于配置git。Git是分布式版本控制系统，所以，每台电脑必须自报家门。

全局配置
```
git config --global user.name 'zjsonic'
git config --global user.email 'zjsonic6@gmail.com'
```
- 参数：--global 本地电脑上的所有仓库都会使用这个配置

本地配置
```
git config user.name 'zjsonic'
git config user.email 'zjsonic6@gmail.com'
```
- 参数：不使用--global，为特定的仓库指定特定的用户名和Email

## 查看全局设置
```
$ git config -l
```
## 初始化本地仓库

```
$ mkdir 'repositoryName'
$ cd 'repositoryName'
$ git init
```


## 把文件提交到本地版本库
第一步：添加队列
```
$ git add  'readme.md'   # 添加一个文件
```
或
```
$ git add  'readme.md' 'file1.md' 'file2.md'  # 添加多个文件
```
或
```
$ git add  .  # 添加所有文件
```

第二步：提交文件
基本使用方法
```
$ git commit -m '版本说明'    # Record changes to the repository 本次提交描述 (之前必须使用git add)
```
其他使用方法
```
$ git commit -a -m '版本说明'  
$ git commit -am '版本说明'  
```
Git 提供了一个跳过使用暂存区域的方式， 只要在提交的时候，给 git commit 加上 -a 选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤


## 查看文件状态
```
$ git status
```

### 查看文件版本不同之处
```
$ git diff custom-select.html
```
>git diff比较的是工作目录中当前文件和暂存区域快照之间的差异， 也就是修改之后还没有暂存起来的变化内容。若要查看已暂存的将要添加到下次提交里的内容，可以用 git diff --cached 命令。

>请注意，git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动。 所以有时候你一下子暂存了所有更新过的文件后，运行 git diff 后却什么也没有，就是这个原因。

## 查看提交日志

```
$ git log   # 显示从最近到最远的提交日志
```

## HEAD参数说明
`HEAD`：是一个指针，表示当前版本。
![HEAD的含义](../../../images/git-head.png)

`HEAD^` ：表示上一个版本
`HEAD^^` ：表示上上一个版本
`HEAD-100` ：表示往上100个版本

## 版本回退

`--hard`:彻底回退到某个版本，本地的源码也会变为上一个版本的内容

```
$ git reset --hard 470f80ed65437c3df6bcf20173772e2abf8aa550  # 回退到版本号的那个版本   
$ git reset --hard HEAD^ # 回退到上一个版本
```

`--soft`:撤销该commit，但是又不能撤销该提交包含的更改
```
$ git reset --soft 470f80ed65437c3df6bcf20173772e2abf8aa550  # 回退到版本号的那个版本   
$ git reset --soft HEAD^ # 回退到上一个版本

```

## 撤销版本回退
`git reset --hard 470f80ed65437c3df6bcf20173772e2abf8aa550`之后，又想撤销回退？

```
git reset --hard 41c645b3d0e9501d82fc834fb839162fd10682bc(回退之前的版本id)
```

## 移除文件

要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除(确切地说，是从暂存区域移除)，然后提交。
可以用git rm命令完成此项工作，并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟踪文件清 单中了。

```
$ git rm filename.md
```
## 从工作目录中手工删除文件
如果只是简单地从工作目录中手工删除文件，运行 git status 时就会在 “Changes not staged for commit” 部分(也就是 未暂存清单)看到:

```
  $ rm PROJECTS.md

  $ git rm PROJECTS.md

```
下一次提交时，该文件就不再纳入版本管理了。



## 删除之前修改过并且已经放到暂存区域

如果删除之前修改过并且已经放到暂存区域的话，则必须要用 强制删除选项 -f(译注:即 force 的首字母)。 这是一种安全特性，用于防止误删还没有添加到快照的数据， 这样的数据不能被 Git 恢复。

## 想让文件保留在磁盘，但是并不想让 Git 继续跟踪
另外一种情况是，我们想把文件从 Git 仓库中删除(亦即从暂存区域移除)，但仍然希望保留在当前工作目录 中。 换句话说，你想让文件保留在磁盘，但是并不想让 Git 继续跟踪。 当你忘记添加 .gitignore 文件，不小 心把一个很大的日志文件或一堆 .a 这样的编译生成文件添加到暂存区时，这一做法尤其有用。 为达到这一目 的，使用 --cached 选项:
```
  $ git rm --cached README
```
git rm命令后面可以列出文件或者目录的名字，也可以使用glob模式。比方说: $ git rm log/\*.log
注意到星号 * 之前的反斜杠 \， 因为 Git 有它自己的文件模式扩展匹配方式，所以我们不用 shell 来帮忙展开。 此命令删除 log/ 目录下扩展名为 .log 的所有文件。 类似的比如:
```
$ git rm \*~
```
该命令为删除以 ~ 结尾的所有文件。



## 移动文件/文件重命名

```
$ git mv file_from file_to
$ git mv a.txt c.txt
```


## 查看本地电脑有没有 SSH 公钥

```
$ cd ~/.ssh // SSH公钥在Mac OS系统下的存储位置
$ ls
authorized_keys2 id_dsa known_hosts
config id_dsa.pub
```
## 创建 SSH 公钥

```
$ ssh-keygen
```
首先 ssh-keygen 会确认密钥的存储位置（默认是 .ssh/id_rsa），然后它会要求你输入两次密钥口令。如果你不想在使用密钥时输入口令，将其留空即可。
现在，进行了上述操作的用户需要将各自的公钥发送给任意一个 Git 服务器管理员（假设服务器正在使用基于公钥的 SSH 验证设置）。 他们所要做的就是复制各自的 .pub 文件内容，并将其通过邮件发送。 公钥看起来是这样的：
```
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAklOUpkDHrfHY17SbrmTIpNLTGK9Tjom/BWDSU
GPl+nafzlHDTYW7hdyZ5ew18JH4JW9jbhUFrviQzM7xlELEVf4h9lFX5QVkbPppSwg0cda3
Pbv7kOdJ/MTyBlWXFCR+HAo3FXRitBqxiX1nKhXpHAZsMciLq8V6RjsNAQwdsdMFvSlVK/7XA
t3FaoJoAsncM1Q9x5+3V0Ww68/eIFmb1zuUFljQJKprrX88XypNDvjYNby6vw/Pb0rwert/En
mZ+AW4OZPnTPI89ZPmVMLuayrD2cE86Z/il8b+gw3r3+1nKatmIkjn2so1d01QraTlMqVSsbx
NrRFi9wrf+M7Q== schacon@mylaptop.local
```

## 将本地库与远程库关联起来

```
$ git remote add origin git@gitserver:zjsonic/learngit.git

```
## 查看远程仓库
```
$ git remote
```

## 删除远程库
```
$git remote remove origin
```

## 推送本地库到远程库
```
$ git push origin master
```

## 配置


```
Quick setup — if you’ve done this kind of thing before
or
HTTPS
SSH

git@github.com:zjsonic/learn-mongodb.git
Get started by creating a new file or uploading an existing file. We recommend every repository include a README, LICENSE, and .gitignore.

…or create a new repository on the command line
echo "# learn-mongodb" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:zjsonic/learn-mongodb.git
git push -u origin master
…or push an existing repository from the command line
git remote add origin git@github.com:zjsonic/learn-mongodb.git
git push -u origin master
…or import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.
```

> - [Git官网](https://git-scm.com/)
