### 同一台pc中gitlab和github共存问题
```
ssh-keygen -t rsa -C "gitlab邮箱账号" // 默认key
ssh-keygen -t rsa -C "github邮箱账号" // 设置key为 id_rsa_github
```
```
然后在.ssh/目录下
touch config
并写入以下内容
# gitlab 公司账号
Host gitlab.com
HostName gitlab.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa

# github 个人账号
Host github.com
User chujian1
HostName ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_github
Port 443
```
```
将生成好的密钥(.pub)对应的添加到gitlab和github的ssh keys中
```
```
注意：
git config --global user.name "1xx"
git config --global user.email "xxx@email.com"
以上命令将1xx这个账号进行了全局设定
所以在项目初次clone下的时候设置下局部账号
git config user.name '2xx'
git config user.email 'xxx@email.com'
这样，当前项目提交的账号就是2xx
否则，提交上去的是全局设置的1xx账号
```

