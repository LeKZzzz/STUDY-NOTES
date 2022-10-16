# Git

------

## 基本原理和特性

Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

采用了分布式版本库的方式，不必服务器端软件支持。

Git把内容按元数据方式存储，而SVN(subversion)是按文件。

Git没有一个全局的版本号。

Git的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。



##	Git 与 SVN 区别

1. Git 不仅仅是个版本控制系统，它也是个内容管理系统(CMS)，工作管理系统等。
2. **Git 是分布式的，SVN 不是**：这是 Git 和其它非分布式的版本控制系统，例如 SVN，CVS 等，最核心的区别。
3. **Git 把内容按元数据方式存储，而 SVN 是按文件：**所有的资源控制系统都是把文件的元信息隐藏在一个类似 .svn、.cvs 等的文件夹里。
4. **Git 分支和 SVN 的分支不同：**分支在 SVN 中一点都不特别，其实它就是版本库中的另外一个目录。
5. **Git 没有一个全局的版本号，而 SVN 有：**目前为止这是跟 SVN 相比 Git 缺少的最大的一个特征。
6. **Git 的内容完整性要优于 SVN：**Git 的内容存储使用的是 SHA-1 哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。

![](E:\Study Notes\Pictures\Git与SVN的区别.jpg)



##	Git GUI、Git Bash、Git CMD之间的区别

1. Git Bash

   1. Bash，Unix shell的一种，Linux与Mac OS X v10.4都将它作为默认shell。
   2. Git Bash就是一个shell，是Windows下的命令行工具，可以执行Linux命令。
   3. Git Bash是基于CMD的，在CMD的基础上增添一些新的命令与功能。所以建议在使用的时候，用Bash更加方便。

2. Git CMD

   （命令行提示符）是Windows操作系统上的命令行解释程序。当你在Windows上安装git并且习惯使用命令行时，可以使用cmd来运行git命令。

3. Git GUI

   基本上针对那些不喜欢黑屏（即命令行）编码的人。它提供了一个图形用户界面来运行您喜欢的git命令。



##	工作流程

###	Git 工作区、暂存区和版本库

1. **工作区：**就是在电脑中看到的目录，可进行添加、编辑、修改文件等操作
2. **暂存区(stage 或 index)**：一般存放在 .git 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引(index)，用以暂存已经修改的文件
3. **版本库(repository)：**工作区有一个隐藏目录 **.git**，这个不算工作区，而是 Git 的版本库，最终确定的文件保存到仓库，成为一个新的版本，并且对别人可见

![](E:\Study Notes\Pictures\Git 工作区、暂存区和版本库)

- 图中左侧为工作区，右侧为版本库。在版本库中标记为 "index" 的区域是暂存区（stage/index），标记为 "master" 的是 master 分支所代表的目录树。
- 图中我们可以看出此时 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。
- 图中的 objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。
- 当对工作区修改（或新增）的文件执行` git add `命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。
- 当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
- 当执行` git reset HEAD` 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
- 当执行 `git rm --cached <file>`命令时，会直接从暂存区删除文件，工作区则不做出改变。
- 当执行 `git checkout . `或者 `git checkout -- <file>` 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。
- 当执行 `git checkout HEAD . `或者` git checkout HEAD <file> `命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。



###	配置

```python
git config --list	# 显示当前的 git 配置信息
git config -e    	# 针对当前仓库
git config -e --global   # 针对系统上所有仓库,如果去掉 --global 参数只对当前仓库有效
git config --global user.name "LeK"	# 配置用户名
git config --global user.email test@XuB.com	# 配置密码
git config --global color.ui auto	# 配置 git 命令输出为彩色的
git config --global merge.tool vimdiff	# 配置解决冲突时使用哪种差异分析工具，比如要使用 vimdiff
git config --global core.editor vi	# 配置 git 使用的文本编辑器
```

系统配置文件位于Git\etc目录下的gitconfig文件

当前登录用户的配置位于C:\Users\username目录下的gitconfig文件



###	创建仓库

Git 使用 `git init` 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 `git init` 是使用 Git 的第一个命令。

在执行完成 `git init` 命令后，Git 仓库会生成一个 .git 隐藏目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。

```python
git init	# 在当前目录生成一个 .git 目录
git init newrepo	# 使用指定目录作为Git仓库
```



###	基本指令

1. `git status`- 查看当前状态，查看在上次提交之后是否有对文件进行再次修改，通常我们使用 **-s** 参数来获得简短的输出结果，**AM** 状态的意思是这个文件在我们将它添加到缓存之后又有改动。

2. ```python
   git add [file1] [file2] ...	# 添加单个或多个文件到暂存区
   
   git add [dir]	# 添加指定目录到暂存区，包括子目录
   
   git add .	# 添加当前目录下的所有文件到暂存区
   ```

3. ```python
   git commit -m "提交说明"	# 将暂存区内容添加到本地仓库中
   
   git commit [file1] [file2] ... -m "提交说明"	# 提交暂存区的指定文件到仓库中
   
   git commit -a	# -a 参数设置修改文件后不需要执行 git add 命令直接提交
   ```

4. 查看提交历史

   1. ```python
      git log	# 查看历史提交记录
      
      git log --oneline	# 用 --oneline 选项来查看历史记录的简洁的版本
      
      git log --graph	# 开启拓扑图选项查看历史中什么时候出现了分支、合并
      
      git log --reverse	# 逆向显示所有日志
      
      git log --auther=authername	# 查找指定用户的提交日志
      ```

      指定日期，可以执行几个选项：--since 和 --before，也可以用 --until 和 --after

   2. `git blame <file> `- 以列表形式查看指定文件的历史修改记录

5. `git reset [--soft | --mixed | --hard] [HEAD]`- 用于回退版本，可以指定退回某一次提交的版本

   1. **--mixed** 参数为默认，可以不用带该参数，HEAD指针指向了要回退的版本，暂存区的文件回滚至之前版本的提交(commit)，工作区文件内容保持不变

      ![](E:\Study Notes\Pictures\git reset --mixed.png)

   2. **--soft** 参数用于回退到某个版本，HEAD指针指向了要回退的版本，工作区和暂存区文件不发生改变，再次提交，会在该版本之上再创建一个新的commit提交，并移动HEAD指针指向的分支来使其指向该commit提交，执行log指令时不会显示回退版本之后提交的信息，但已提交的内容不会被删除，使用reflog命令可查看

      ![](E:\Study Notes\Pictures\git reset --soft 1.png)

      ![](E:\Study Notes\Pictures\git reset --soft 2.png)

   3. **--hard** 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除该回退版本之后所有的信息提交，执行log指令时不会显示回退版本之后提交的信息，但已提交的内容不会被删除，使用reflog命令可查看

      ![](E:\Study Notes\Pictures\git reset --hard.png)

   4. `git reset HEAD [filename]`- 用于取消已缓存的内容

      1. - HEAD 表示当前版本
         - HEAD^ 上一个版本
         - HEAD^^ 上上一个版本
         - HEAD^^^ 上上上一个版本
         - 以此类推...
      2. - HEAD~0 表示当前版本
         - HEAD~1 上一个版本
         - HEAD^2 上上一个版本
         - HEAD^3 上上上一个版本
         - 以此类推...

6. `git clone [url]`- 拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改

   默认情况下，Git 会按照提供的 URL 所指向的项目的名称创建本地项目目录。 通常就是该 URL 最后一个 / 之后的项目名称。如果你想要一个不一样的名字， 你可以在该命令后加上你想要的名称

7. 当项目过大时，git clone时会出现error: RPC failed; HTTP 504 curl 22 The requested URL returned error: 504 Gateway Time-out的问题，解决方法很简单，在git clone时加上--depth=1即可解决:depth用于指定克隆深度，为1即表示只克隆最近一次commit.

   

7. ```python
   git diff [file]	# 比较文件的不同，即比较文件在暂存区和工作区的差异
   
   git diff --cached [file]	# 显示暂存区和上一次提交(commit)的差异
   
   git diff [first-branch]...[second-branch]	# 显示两次提交之间的差异
   
   git diff HEAD	# 查看已缓存的与未缓存的所有改动
   
   git diff --stat	# 显示摘要而非整个 diff
   ```

   

8. ```python
   git rm <file>	# 将文件从暂存区和工作区中删除
   
   git rm -f <file>	# 强行从暂存区和工作区中删除修改后的文件
   
   git rm --cached <file>	# 把文件从暂存区域移除，即仅是从跟踪清单中删除
   
   git rm –r *	# 递归删除整个目录中的所有子目录和文件
   ```

9. `git show`- 可以查看commit的详细信息

10. `git revert`以撤销指定的提交内容，撤销后会生成一个新的commit

    1. revert 常规commit：

       使用 `git revert <commit id>` 即可，git 会生成一个新的 commit，将指定的 commit 内容从当前分支上撤除

    2. revert merge commit：

       revert merge commit 有一些不同，这时需要添加 `-m` 选项以代表这次 revert 的是一个 merge commit

       `git revert -m commitnumber commitid`-  -m 选项接收的参数是一个数字，数字取值为 1 和 2，也就是 Merge 行里面列出来的第一个还是第二个，其含义用来保留某个分支

11. 

    ```python
    git remote -v	# 显有所有远程仓库
    git remote show [remote]	# 显示某个远程仓库的信息
    git remote add [shortname] [url]	# 添加远程版本库
    git remote rm name	# 删除远程仓库
    git remote rename old_name new_name	# 修改仓库名
    ```

    **origin** 为远程地址的别名

12. `git fetch [alias]`- 从远程获取代码库，该命令执行完后需要执行 git merge 远程分支合并到当前所在的分支

13. `git pull <远程主机名> <远程分支名>:<本地分支名>`- 用于从远程获取代码并合并本地的版本，即`git fetch` 和 `git merge FETCH_HEAD` 的简写，如果远程分支是与当前分支合并，则冒号后面的部分可以省略

14. `git push <远程主机名> <本地分支名>:<远程分支名>`- 用于从将本地的分支版本上传到远程并合并，如果本地分支名与远程分支名相同，则可以省略冒号

    `git push --force <远程主机名> <本地分支名>:<远程分支名>`- 如果本地版本与远程版本有差异，但又要强制推送可以使用 --force 参数



###	分支管理

> 1. 主分支（master）：第一次向 git 仓库提交更新记录时自动产生的一个分支。
> 2. 开发分支（develop）：作为开发的分支，基于 master 分支创建。
> 3. 功能分支（feature）：作为开发具体功能的分支，基于开发分支创建。

####	基础操作

1. `git branch`- 查看分支，当前分支前会有"*"标记

1. `git branch (branchname)`- 创建分支

   `git branch -d (branchname)`- 删除分支，删除时需要被删除分支不处于使用状态

2. `git checkout (branchname)`- 切换分支，切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录

   ` git checkout -b (branchname)`- 创建新分支并立即切换到该分支下

4. `git merge (branchname)` - 用来进行分支合并，将其他分支中的内容合并到当前分支中

   `git merge --no-ff (branchname)`- 用来进行快进合并(fast-forward merge)

5. `git branch -m 旧名字 新名字`- 修改分支名

6. `git push origin --delete (branchname)`- 删除远程分支

3. `git branch -dr [remote/branch]`- 删除远程分支



####	冲突的产生和解决

> 合并并不仅仅是简单的文件添加、移除的操作，Git 也会合并修改
>
> 远程仓库和本地仓库文件内容不一致且对方版本并不在自身版本库中，或当Git发现某一块数据在两个分支间的提交历史中都含有变更，此时执行push/pull/merge会产生冲突
>
> 如远程仓库的版本为基于V1开发的V2，本地仓库的版本为基于V1开发的V3，此时push V3或pull V2便会产生冲突

解决：

1. `git pull`，此时Git会将线上与本地仓库的冲突合并到对应的文件中，且在冲突位置做出标记
2. 手动解决冲突
3. `git push`



##	忽略文件

忽略文件需要新建一个名为**.gitignore**的文件，该文件用于声明忽略文件或不忽略文件的规则，规则对当前目录及其子目录有效。

> 该文件因为没有文件名，因此没办法直接在Windows目录下直接创建，可以通过git bash的touch命令创建
>
> .gitignore规则
>
> > /mtk/        过滤整个文件夹
> > *.zip         过滤所有.zip文件
> > /mtk/file     过滤某个具体文件
> >
> > !*.zip			添加所有.zip文件到版本管理
> > !/mtk/file		添加某个具体文件到版本管理
> >
> > 注释应用"#"标记
> >
> > - 以斜杠“/”开头表示目录
> >
> >    注意，不管是根目录下的同名目录，还是某个子目录的同名目录，都会被忽略
> >
> > - 以星号“*”通配多个字符
> >
> > - 以问号“?”通配单个字符
> >
> > - 以方括号“[]”包含单个字符的匹配列表；
> >
> > - 以叹号“!”表示不忽略(跟踪)匹配到的文件或目录；
>
> 如果不慎在创建.gitignore文件之前就push了项目，那么即使在.gitignore文件中写入新的过滤规则，这些规则也不会起作用，Git仍然会对所有文件进行版本管理。



#	Github

> GitHub 是一个面向开源及私有软件项目的托管平台，因为只支持 Git 作为唯一的版本库格式进行托管，故名 GitHub。
>
> GitHub 于 2008 年 4 月 10 日正式上线，除了 Git 代码仓库托管及基本的 Web 管理界面以外，还提供了订阅、讨论组、文本渲染、在线文件编辑器、协作图谱（报表）、代码片段分享（Gist）等功能。目前，其托管版本数量非常之多，而且其中不乏知名开源项目，例如 Ruby on Rails、jQuery、python 等。
>
> 作为开源代码库以及版本控制系统，Github 拥有超过千万的开发者用户。随着越来越多的应用程序转移到了云上，Github 已经成为了管理软件开发以及发现已有代码的首选方法。
>
> 如前所述，作为一个分布式的版本控制系统，在 Git 中并不存在主库这样的概念，每一份复制出的库都可以独立使用，任何两个库之间的不一致之处都可以进行合并。
>
> GitHub 可以托管各种 Git 库，并提供一个 web 界面，但与其它像 SourceForge 或 Google Code 这样的服务不同，GitHub 的独特卖点在于从另外一个项目进行分支的简易性。为一个项目贡献代码非常简单：首先点击项目站点的Fork的按钮，然后将代码检出并将修改加入到刚才分出的代码库中，最后通过内建的pull request机制向项目负责人申请代码合并。
>
> GitHub 项目本身自然而然的也在 GitHub 上进行托管，只不过在一个私有的，公共视图不可见的库中。开源项目可以免费托管，但私有库则并非如此。

##	基础概念

**Repository**：简称Repo，可以理解为“仓库”，我们的项目就存放在仓库之中。也就是说，如果我们想要建立项目，就得先建立仓库；有多个项目，就建立多个仓库。

**Issues**：可以理解为“问题”，举一个简单的例子，如果我们开源一个项目，如果别人看了我们的项目，并且发现了bug，或者感觉那个地方有待改进，他就可以给我们提出Issue，等我们把Issues解决之后，就可以把这些Issues关闭；反之，我们也可以给他人提出Issue。

**Star**：可以理解为“点赞”，当我们感觉某一个项目做的比较好之后，就可以为这个项目点赞，而且我们点赞过的项目，都会保存到我们的Star之中，方便我们随时查看。在 GitHub 之中，如果一个项目的点星数能够超百，那么说明这个项目已经很不错了。

**Fork**：可以理解为“拉分支”，如果我们对某一个项目比较感兴趣，并且想在此基础之上开发新的功能，这时我们就可以Fork这个项目，这表示复制一个完成相同的项目到我们的 GitHub 账号之中，而且独立于原项目。之后，我们就可以在自己复制的项目中进行开发了。

**Pull Request**：可以理解为“提交请求”，此功能是建立在Fork之上的，如果我们Fork了一个项目，对其进行了修改，而且感觉修改的还不错，我们就可以对原项目的拥有者提出一个Pull请求，等其对我们的请求审核，并且通过审核之后，就可以把我们修改过的内容合并到原项目之中，这时我们就成了该项目的贡献者。

**Merge：**可以理解为“合并”，如果别人Fork了我们的项目，对其进行了修改，并且提出了Pull请求，这时我们就可以对这个Pull请求进行审核。如果这个Pull请求的内容满足我们的要求，并且跟我们原有的项目没有冲突的话，就可以将其合并到我们的项目之中。当然，是否进行合并，由我们决定。

**Watch：**可以理解为“观察”，如果我们Watch了一个项目，之后，如果这个项目有了任何更新，我们都会在第一时候收到该项目的更新通知。

**Gist：**如果我们没有项目可以开源或者只是单纯的想分享一些代码片段的话，我们就可以选择Gist。



## 协议

| 协议      | 简述                                                         |
| --------- | ------------------------------------------------------------ |
| Apache    | 允许他人修改源代码后再闭源，但是必须对每个修改过的文件做版权说明 |
| GPL3      | 无论以何种方式修改或者使用代码，都需要开源                   |
| MIT       | 允许他人修改源代码后再闭源，不用对修改过的文件做说明，且二次开发的软件可以使用原作者的名字做营销 |
| BSD2/BSD3 | 和上面一条类似，但未经事先书面许可，不得使用版权所有者的姓名或其贡献者的姓名来推广 |
| BSL       | 和GPL类似，但不需要复制版权信息                              |
| CCZ       | 放弃创作的作品版权权益，并将其奉献给大众，不对代码做任何担保 |
| EPL       | 与GPL类似，有权使用、修改、复制与发布软件原始版本和修改后版本，但在某些情况下则必须将修改内容一并释出 |
| AGPL      | GPL拓展，使用在线网络服务的也需要开源                        |
| GPL2      | 和GPL3相比，如果使用代码作为服务提供，而不分发软件，则不需要开源 |
| LGPL      | 和GPL相比，LGPL允许商业软件通过类库引用(link)方式使用LGPL类库而不需要开源商业软件的代码 |
| Mozilla   | 与LGPL类似，但是需要对修改过的源码内容做说明                 |
| Unlicense | 与CCZ相似，且开放商标和所用的专利授权                        |



##	GIthub Pages

> GitHub.io 就是GitHub Pages，GitHub Pages 是一种静态站点托管服务，它直接从 GitHub 上的存储库获取 HTML、CSS 和 JavaScript 文件，可选择通过构建过程运行文件，然后发布网站。
>
> github pages有300M免费空间，资料自己管理，保存可靠
>
> 它的 URL 采用 username.github.io/my-repository-name 的格式

1. `Settings -》GitHub Pages`
2. `Choose a theme` 按钮可以帮你选择一个网站主题
