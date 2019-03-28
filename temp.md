# 集中式VS分布式
我是这么理解，这里有几个概念：本地、服务器、中央服务器（远程服务器）。每一次commit是提交到本本机的服务器，这个不需要联网，正所谓的版本管理，就是要方便我们知道每一个版本，比如回到之前的某个版本（这是其一），而且回退到某个之前的版本，也是从本机的服务器拿的数据，这些都不需要联网。而 SVN 的每一次 commit 都需要联网，这就需要网络的等待。 Git只有在Push、pull 的时候需要联网，而我们平时更多的操作应是commit。再有就是，断网的情况下，SVN也能工作，但是由于没有版本控制的记录，当多人修改后就比较难以快速的合并，但是Git都在本地保存了版本记录，所以大家合并起来就方便得多了。

# git config
```
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。你也许会担心，如果有人故意冒充别人怎么办？这个不必担心，首先我们相信大家都是善良无知的群众，其次，真的有冒充的也是有办法可查的。

注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。


# git init 创建版本库
```
git init
```


# git add 添加到暂存区
```
git add readme.md
```

执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

## 为什么需要git add
Git作为目前逼格最高的源代码管理工具，SVN（netease实习时候用）这个优良的特性显然是要借鉴的。但是Linus马上发现了一个麻烦事儿，在命令行下面选择要提交的修改，还真TM是个麻烦事儿，因为用SVN的时候我们都是这么玩的：

GUI界面勾选需要commit的文件，再原子性提交。

显然这点小问题完全难不倒Linus这么一位旷世奇才。我们只需要在commit前面，发明一个暂存区（Stage）的概念就好了，这个暂存区是可以随意的将各种文件的修改放进去的，这样我们就可以用多个指令精确的挑选出我们需要提交的所有修改，然后再一次性的（原子性的）提交到版本库，问题就完美的解决了。

工作区 -> 暂存区 -> 版本库


# git commit 提交到本地仓库
```
git commit -m "wrote a readme file"
```


# git status 查看仓库当前状态
```
git status
```
```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   readme.md

no changes added to commit (use "git add" and/or "git commit -a")
```


# git diff 具体查看修改内容
```
git diff readme.md
```
```
diff --git a/readme.md b/readme.md
index 46d49bf..9247db6 100644
--- a/readme.md
+++ b/readme.md
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```
可以从上面的命令输出看到，在第一行添加了一个`distributed`单词

`git diff` 比较的是工作区文件与暂存区文件的区别（上次git add 的内容）

`git diff --cached` 比较的是暂存区的文件与仓库分支里（上次git commit 后的内容）的区别

```
——————    —    —    —    —    —    —
|     版本库     |                  |
——————    —    —    —    —    —    —
.            |                     |
.    git diff --cached             |   
.    git diff --staged             |
.            |                     |
——————    —    —    —    —    —    |
|     暂存区     |             git diff head
——————  —    —    —    —    —      |
.           |                      |
.        git diff                  |
.           |                      |
——————  —    —    —    —    —      |
|     工作区     |                  |
——————    —    —    —    —    —    —
```


# git log 查看提交历史记录
```
git log
```
```
commit 1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master)
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:06:15 2018 +0800

    append GPL

commit e475afc93c209a690c39c13a46716e8fa000c366
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:03:36 2018 +0800

    add distributed

commit eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 20:59:18 2018 +0800

    wrote a readme file
```
详细显示了 版本号、作者、日期、提交说明

## git log --pretty=online 减少日志输出信息
```
git log --pretty=oneline
```
```
1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL
e475afc93c209a690c39c13a46716e8fa000c366 add distributed
eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file
```
只显示了版本号和提交说明


# git reset 回退到指定版本
```
git reset --hard HEAD^
```
```
HEAD is now at e475afc add distributed
```
首先，Git必须知道当前版本是哪个版本，

在Git中，用`HEAD`表示当前版本，也就是最新的提交1094adb...（注意我的提交ID和你的肯定不一样），

上一个版本就是`HEAD^`，

上上一个版本就是`HEAD^^`，

当然往上100个版本写100个^比较容易数不过来，所以写成`HEAD~100`

## git reset --hard commitId 回退到commitId版本
最新的那个版本append GPL已经看不到了！好比你从21世纪坐时光穿梭机来到了19世纪，想再回去已经回不去了，肿么办？

办法其实还是有的，只要上面的命令行窗口还没有被关掉，你就可以顺着往上找啊找啊，找到那个append GPL的commit id是1094adb...，于是就可以指定回到未来的某个版本：
```
git reset --hard 1094a
HEAD is now at 83b0afe append GPL
```

## git reflog 记录之前操作git的每一次命令

```
git reflog
```
```
e475afc HEAD@{1}: reset: moving to HEAD^
1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
e475afc HEAD@{3}: commit: add distributed
eaadf4e HEAD@{4}: commit (initial): wrote a readme file
```
这边记录了三次操作，两次commit，一次回退
从输出可知，append GPL的commit id是1094adb，现在，你又可以乘坐时光机回到未来了。

## 只恢复一个文件的办法
git reset --hard 1094a的分支上可能有很多的文件，比如文件1 2 3 4... 而我只想恢复文件1在1094a上的内容，应该怎么操作。

从最新版恢复到1094a，把文件1复制出来

再恢复回最新版，把文件1覆盖进去

提交文件1的改动


# git checkout -- file 撤销工作区的内容
```
git checkout -- readme.md
```

只对工作区的内容进行回退到版本库最近的，如果已经`git add`（但没有`git commit`）则没有效果。

（若是一个文件其中有一部分git add，则相应部分不会被回退，其他未git add回退）

（存储在暂存区的内容就好比让这条命令知道，这行不需要回退，除非你删了暂存区的这部分内容）

`git checkout -- file`命令中的`--`很重要，没有`--`，就变成了“切换到另一个分支”的命令


# git reset HEAD <file> 撤销暂存区的内容

```
git reset HEAD readme.md
```
只是删去了暂存区里的内容。

进行小测试。

1. 修改文本，添加到暂存区（git add）
2. 输入'git checkout -- readme.md'，没有反应。
3. 当敲'git reset HEAD readme.md'命令的时候，你会发现，文本内容没有改变，但是使用`git status`发现，修改变为红色，表示没有添加到暂存区。
4. 此时再调用一次'git check -- readme.md'，工作区的内容删去。

## 小结
- 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

- 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

- 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退，不过**前提是没有推送到远程库**。


# git rm file 删除文件
```
git rm test.md
```
小测试，如果已经添加到版本库，则会删去工作区的test.md，放置到暂存区。

如果只`git add`暂存区，会删去暂存区和工作区的test.md。

其实就是相当于帮忙做了两步操作，`rm file``git add .`没有什么新意。（之所以第二种情况 working tree clean，本来就没有添加到版本库，只是删了一个刚新建的文件，所以git add .也是为空，没有新增任何文件，所以两种情况的本质是抑制的）


# git remote add 添加远程仓库
```
git remote add origin https://github.com/514723273/XXX.git
git push -u origin master
```
-u

git push --set-upstream origin master

加了参数-u后，以后即可直接用git push 代替git push origin master


# git rebase 变基

只对尚未推送或分享给别人的本地修改执行变基操作清理历史；

从不对已推送至别处的提交执行变基操作

我就是BUG 快来删掉我 这就是冲突

是拉去远程仓库分支代码
