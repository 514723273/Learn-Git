## 安装Git
|Git命令|地址|补充|
| --- | --- | --- |
|`git config --global user.name "Your Name"`|[安装Git](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)|配置名字和Email地址|


## 创建版本库
|Git命令|地址|补充|
| --- | --- | --- |
|`git init`|[创建版本库](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743256916071d599b3aed534aaab22a0db6c4e07fd0000)|创建版本库|
|`git add readme.md`|[创建版本库](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743256916071d599b3aed534aaab22a0db6c4e07fd0000)|添加到暂存区|
|`git commit -m "add readme.md"`|[创建版本库](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743256916071d599b3aed534aaab22a0db6c4e07fd0000)|提交到本地仓库|


## 时光机穿梭
|Git命令|地址|补充|
| --- | --- | --- |
|`git status`|[时光机穿梭](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743858312764dca7ad6d0754f76aa562e3789478044000)|查看仓库当前状态|
|`git log`|[版本回退](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000)|查看提交历史记录|
|`git reset --hard HEAD^`|[版本回退](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000)|回退到指定版本|
|`git reflog`|[版本回退](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000)|显示之前操作过Git版本的所有命令|
|`git diff readme.md`|[管理修改](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374829472990293f16b45df14f35b94b3e8a026220c5000)|具体查看修改内容|
|`git checkout -- readme.md`|[撤销修改](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374831943254ee90db11b13d4ba9a73b9047f4fb968d000)|撤销工作区的内容|
|`git reset HEAD readme.md`|[撤销修改](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374831943254ee90db11b13d4ba9a73b9047f4fb968d000)|撤销暂存区的内容|
|`git rm readme.md`|[删除文件](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374831943254ee90db11b13d4ba9a73b9047f4fb968d000)|删除文件|


## 远程仓库
|Git命令|地址|补充|
| --- | --- | --- |
|`git remote add origin https://github.com/514723273/Learn-Git.git`|[添加远程库](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000)|添加远程仓库|
|`git clone`|[从远程库克隆](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375233990231ac8cf32ef1b24887a5209f83e01cb94b000)|克隆仓库|


## 分支管理
|Git命令|地址|补充|
| --- | --- | --- |
|`git branch`|[创建与合并分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)|查看分支|
|`git branch <branchName>`|[创建与合并分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)|创建分支|
|`git checkout <branchName>`|[创建与合并分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)|切换分支|
|`git checkout -b <branchName>`|[创建与合并分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)|创建+切换分支|
|`git merge <branchName>`|[创建与合并分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)|合并某分支到当前分支|
|`git branch -d <branchName>`|[创建与合并分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)|删除分支|
|`git merge --no-ff -m "" dev`|[分支管理策略](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758410364457b9e3d821f4244beb0fd69c61a185ae0000)|禁用`Fast forward`|
|`git stash`|[Bug分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)|把当前工作现场“储藏”起来（即版本最初始状态）（用于切换分支解决其他问题，返回现场）|
|`git stash pop`|[Bug分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)|取出所有的修改|
|`git branch -D <branchName>`|[Feature分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376026233004c47f22a16d1f4fa289ce45f14bbc8f11000)|强行删除（大写的`-D`参数）|
|`git checkout -b dev origin/dev`|[多人协作](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013760174128707b935b0be6fc4fc6ace66c4f15618f8d000)|基于远程分支创建本地分支|

## 标签管理
|Git命令|地址|补充|
| --- | --- | --- |
|``|[]()||
|``|[]()||
|``|[]()||
|``|[]()||
|``|[]()||
|``|[]()||
|``|[]()||