
# 首次配置初始化相关
## 创建本地仓库并初始化(以指定文件夹 D:\answer文件夹为例)
cd /d D:\answer             切换至指定文件夹(change directory)
mkdir LearnGit              创建文件夹
git init                    初始化仓库


## 配置用户名和邮箱(电脑首次使用git,也可以用来修改用户名和邮箱)
git config --global user.email"you@example.com"
git config --global user.name"your name"

## 添加远程仓库(两种连接方式https/ssh, https 不稳定/每次都要进行验证所以一般使用ssh)

git remote -v                       查看当前远程仓库地址
ls ~/.ssh                           查看是否具有SSH key
## 如果显示 id_rsa  id_rsa.pub  known_hosts  known_hosts.old 表示已经有ssh key

ssh-keygen -t rsa -b 4096 -C "你的GitHub邮箱"       生成ssh key (一路回车默认不设置密码)

## 启动 ssh-agent
eval "$(ssh-agent -s)"

## 添加私钥到 ssh-agent
ssh-add ~/.ssh/id_rsa

## 复制公钥粘贴上传到github/Giteee等代码管理平台
cat ~/.ssh/id_rsa.pub

## 登录 GitHub → 点击右上角头像 → Settings，左侧菜单 → SSH and GPG keys → New SSH key,Title 随便填（如 "My Laptop"），Key 里粘贴刚复制的内容 → 保存

## 测试链接
ssh -T git@github.com

Are you sure you want to continue connecting (yes/no)? 第一次会问
输入 yes 显示: You've successfully authenticated... 表示配置成功

git add remote LearnGit <url>    

## 修改远程仓库地址为ssh
git remote set-url Github git@github.com:xxxx/python_algorithm.git

