# GIT

## git文件的三种状态
- committed: 文件已经安全的保存在库中。
- modified: 文件已修改但未保存在库中。
- staged: 文件已加入提交快照中。

## git的三个区
- 工作区：git init命令所在目录(在工作区中修改文件)
- 暂存区：是一个文件：.git/index，保存了下次提交的文件列表信息。(将快照放入暂存区)
- 版本库：是一个目录：.git 保存元数据和对象数据的地方(提交更新，将快照永久存储在git仓库)


## 安装git (第一步)
```
$ git //检查有无安装git
$ git --version //查看git版本
$ sudo apt-get install git //Fedora上安装git
$ sudo yum install git //Debian和ubuntu上安装git
$ git //Mac上安装git(直接运行即可)Mavericks （10.9)以上的
```

## git config (第二步)
`git config`: 设置git外观和行为的配置变量。这些变量存储在三个位置：
- `.git/config`文件: 针对当前库
- `~/.gitconfig`文件:针对当前用户
- `/etc/gitconfig`文件: 针对所有用户
注意：每一级别覆盖上一级别

**检查所有配置信息**
```
$ git config --global  -l //检查当前用户的所有配置信息
$ git config -l // 检查当前库的所有配置信息
```

**设置当前用户的配置变量**

适用于电脑上只有一个git账号，多个版本库，本地电脑上的所有仓库都会使用这个配置。
```
$ git config --global user //检查当前用户的某一项配置信息
$ git config --global user.email //检查当前用户的某一项配置信息
$ git config --global user.name 'zhangjie' //设置当前用户的名字
$ git config --global user.email 'yeszhangjie@gmail.com' //设置当前用户的电子邮件
$ git config --global core.editor emacs //设置当前用户的默认编辑器为emacs
```

**设置当前库的配置变量**

适用于电脑上有两个以上的git账号。
```
$ git config  user //检查当前库的某一项配置信息
$ git config  user.email //检查当前库的某一项配置信息
$ git config  user.name 'zhangjie' //设置当前库的名字
$ git config  user.email 'yeszhangjie@gmail.com' //设置当前库的电子邮件
```

## 创建git仓库(第三步)
有两种取得 Git 项目仓库的方法。 第一种是在现有项目或目录下导入所有文件到 Git 中； 第二种是从一个服务器克隆一个现有的 Git 仓库。
**git init**

```
$ git init
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```
**git clone**
```
$ git clone https://github.com/libgit2/libgit2 //克隆远程仓库
$ git clone https://github.com/libgit2/libgit2 mylibgit  //克隆远程仓库 自定义本地仓库名

```

## .gitignore(第四步)
版本库的根目录下创建`.gitignore`文件
```
# Numerous always-ignore extensions  
*.bak  
*.patch  
*.diff  
*.err  

# temp file for git conflict merging  
*.orig  
*.log  
*.rej  
*.swo  
*.swp  
*.zip  
*.vi  
*~  
*.sass-cache  
*.tmp.html  
*.dump  

# OS or Editor folders  
.DS_Store  
._*  
.cache  
.project  
.settings  
.tmproj  
*.esproj  
*.sublime-project  
*.sublime-workspace  
nbproject  
thumbs.db  
*.iml  

# Folders to ignore  
.hg  
.svn  
.CVS  
.idea  
node_modules/  
jscoverage_lib/  
bower_components/  
dist/
```

## git status
```
$ git status
```

## git add
`git add`: Track the file,otherwise, the file is untracked.
```
$ git add  'readme.md'   # 添加一个文件
$ git add  'readme.md' 'file1.md' 'file2.md'  # 添加多个文件
$ git add  .  # 添加所有文件
```

## git commit
```
$ git commit -m '版本说明'    # Record changes to the repository 本次提交描述 (之前必须使用git add)
$ git commit -a -m '版本说明'  
$ git commit -am '版本说明'
$ git commit --amend //commit amend:本次提交将代替上一次提交的结果(撤销上一次提交，重新提交)
```

## git ls-files
`git ls-files`: 查看暂存区中的文件信息。
```
$ git ls-files //查看暂存区文件列表
$ git ls-files --cached //查看暂存区文件列表 默认参数
$ git ls-files --stage //获取暂存区中文件的内容
$ git ls-files -s // --stage的简写
$ git ls-files --modified // 显示修改过的文件
```
## git log
`git log`: show the commit logs
```
$ git log  //显示从最近到最远的提交日志
$ git log
```

### git diff
```
$ git diff custom-select.html
```

## HEAD参数说明
`HEAD`：是一个指针，表示当前版本。
![HEAD的含义](../../../images/git-head.png)

`HEAD^` ：表示上一个版本
`HEAD^^` ：表示上上一个版本
`HEAD-100` ：表示往上100个版本


## git checkout
`git checkout`: Restore the working tree files
```
$ git checkout -- file_name  // 1.从版本库拉取文件替换工作区文件 2.从暂存区拉取文件替换工作区文件(如果有)
```

## git reset

```
$ git reset HEAD file_name   //取消某个暂存区的文件(比如，git add了两个，在commit之前发现想撤销其中一个的暂存)
```

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


## git rm
`git rm`: unstage
```
$ git rm --cached file_to_be_unstaged  // to unstage
```

要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除(确切地说，是从暂存区域移除)，然后提交。
可以用git rm命令完成此项工作，并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟踪文件清 单中了。

```
$ git rm filename.md
```

如果只是简单地从工作目录中手工删除文件，运行 git status 时就会在 “Changes not staged for commit” 部分(也就是 未暂存清单)看到:

```
  $ rm PROJECTS.md

  $ git rm PROJECTS.md

```
下一次提交时，该文件就不再纳入版本管理了。



删除之前修改过并且已经放到暂存区域

如果删除之前修改过并且已经放到暂存区域的话，则必须要用 强制删除选项 -f(译注:即 force 的首字母)。 这是一种安全特性，用于防止误删还没有添加到快照的数据， 这样的数据不能被 Git 恢复。

想让文件保留在磁盘，但是并不想让 Git 继续跟踪
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

## git mv
```
$ git mv file_from file_to
$ git mv a.txt c.txt
```

## git remote

```
$ git remote //查看远程仓库的简写
$ git remote -v //查看远程仓库的简写和地址
$ git remote add <shortname> <url> //添加新的git远程仓库
$ git remote add pb https://github.com/paulboone/ticgit //
$ git remote add origin git@gitserver:zjsonic/learngit.git
$ git remote rename <oldname> <newname> //修改远程仓库的名称
$ git remote rename pb paul //
$ git remote rm <name> //删除库
$ git remote rm paul
$ git remote remove origin

```

## git push
```
$ git push [remote-name] [branch-name] //当你想要将 master 分支推送到 origin 服务器时
$ git push origin master
```



## Github新库提示信息

```
Quick setup — if you’ve done this kind of thing before
- HTTPS
- SSH

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
