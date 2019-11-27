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
  
