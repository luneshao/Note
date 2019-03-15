# ssh key 管理

  进来需要同时使用 GitHub 和 GitLab。想把私钥管理的明明白白的，然后就找了教程。建立了两个私钥，并添加了配置文件管理。
  
  管理过程如下：
  
* 新建公私钥对
  
```
  ssh-keygen -t rsa -C "youremail@gmail.com"
```

tip:注意，此处会需要输入一个<b>创建密码</b>，请<b>记住这个密码</b>。因为一会push的时候会提示需要输入。
我直接用的 <i>`id_rsa_gitlab`</i>，不容易忘。。
  
* 添加私钥，为方便每次获取
  
```
  ssh-add ~/.ssh/id_rsa
  ssh-add ~/.ssh/id_rsa_github
```

* 新建 config 文件，并且为 GitHub 、 GitLab 配置对应的私钥文件。

```
vi config

# gitlab
Host gitlab.com
    HostName gitlab.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa

# github
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github
```

* 测试

```
ssh git@gitlab.com
```

如果输出：`<i>Welcome to GitLab, @luneshao!</i>` 那么你就成功辣。
