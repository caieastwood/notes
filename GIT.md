## Git

### 生成SSH key
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

### 查看SSH keys公钥
`cat ~/.ssh/id_rsa.pub`

### 查看用户配置
`git config --global -l`

### 编辑用户配置
`git config --global -e`

### 添加配置项目
`git config --global user.email "you@example.com"`
`git config --global user.name "Your Name"`

### 修改commit信息
> 修改最后一次提交信息  
`git commit --amend`  
> 修改某次提交的信息  
1 `git rebase -i HEAD~2` 2表示显示倒数第一次和倒数第二次的提交信息，想要修改哪条注释，就把哪条注释前面的pick改成edit，wq保存退出  
2 `git commit --amend` 改成edit的那一次提交会变成最后一次提交，使用修改最后一次提交注释的方法修改  
3 `git rebase --continue` 修改完成保存退出后需要continue  
4 `git push --force origin master` 如commit已经push到remote，则需要重新push一次  

### 挑拣
`git cherry-pick xxxxxx` 挑拣其他分支的某个提交的内容合并到本分支并自动提交  
`git cherry-pick -n xxxxxx` 挑拣其他分支的某个提交的内容合并到本分支，加上-n之后则不自动提交  
`git cherry-pick -e xxxxxx` 挑拣其他分支的某个提交的内容合并到本分支，加上-e之后则会重新编辑提交信息  
`git cherry-pick xxxxxx -m 1` 以下为例子：  
master A-B-C-X  
fix A-B-C-Y  
master merge fix后，master变成A-B-C-X-Z，其中Z为merge类型的commit，其中包含了Y的改动  
此时有一条新的分支feature A-B-C  
cherry-pick Z -m 1，表明Z的父节点为第一个父节点，即X，此时pick这个merge的内容是X如何到Z，即Y的内容（Z包含X和Y），所以pick的是Y的提交，变成A-B-C-Y  
cherry-pick Z -m 2，表夫Z的父节点为第二个父节点，即Y，此时pick这个merge的内容是Y如何到Z，即X的内容（Z包含X和Y），所以pick的是X的提交，变成A-B-C-X  
同理可得，如果是feature A-B-C-X，此时cherry-pick Z也要选择父节点，那就要用cherry-pick Z -m 1，如果是-m 2则不会有任何变化，因为feature已经包含了X  

### 临时保存 恢复修改
`git stash` or `git stash save "message"` 直接保存或保存并添加message，添加message可以在之后方便找到对应的修改并恢复  
`git stash list` 查看保存的记录列表  
`git stash show` or `git stash show stash@{index} -p` 查看做了哪些改动，默认显示第一条记录，也能通过index查找特定的一条记录，加上-p可以查看更加详细的修改内容  
`git stash pop` or `git stash pop stash@{index}` 直接恢复或恢复编号为index的记录，恢复之后即将此记录从stash列表删除  
`git stash apply` or `git stash apply stash@{index}` 直接恢复或恢复编号为index的记录，恢复之后此记录将在stash列表继续保留  
`git stash drop` or `git stash drop stash@{index}` 删除全部或从stash列表种删除编号为index的记录  
`git stash clear` 删除保存的所有记录  

### reset和revert
`git reset --hard HEAD^` 重置branch到上一次提交，会将stage区（即add之后的区域，绿色部分）和工作目录（即还未add的区域，红色部分）内的内容都重置掉  
`git reset --soft HEAD^` 重置branch到上一次提交，重置前的stage区和工作目录的内容会被保留，被重置掉的commit的改动会被add到stage区  
`git reset --mixed HEAD^` git reset不加参数即默认使用--mixed，重置branch到上一次提交，stage区的内容被放到工作目录并清空，被重置掉的commit的改动也会被放到工作目录，即将所有的差异混合在一起放到工作目录  
`git reset` 效果等同于git reset --mixed HEAD，即回退到当前版本，并将修改放回工作目录，用于撤销错误add  

如果远程分支是受保护的，即不允许force push，则需要产生一个新的commit来撤销之前的commit（可以跨过已提交的commit），则使用revert命令  
`git revert commit1...` 回滚一条或多条commit，回滚后改动自动提交  
`git revert -n commit1...` 回滚一条或多条commit，-n即--no-commit，回滚的改动不自动提交，会将回滚的commit放到stage区，需要手动git commit一下  