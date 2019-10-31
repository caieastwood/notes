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

`git commit --amend`