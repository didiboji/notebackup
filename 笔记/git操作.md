### git操作



## Git add

 git add [参数] <路径>　作用就是将我们需要提交的代码从工作区添加到暂存区，就是告诉git系统，我们要提交哪些文件，之后就可以使用git commit命令进行提交了。



git commit -m ‘message’

-m 参数表示可以直接输入后面的“message”，如果不加 -m参数，那么是不能直接输入message的，而是会调用一个编辑器一般是vim来让你输入这个message，

message即是我们用来简要说明这次提交的语句。



## Git push

 在使用git commit命令将修改从暂存区提交到本地版本库后，只剩下最后一步将本地版本库的分支推送到远程服务器上对应的分支了。
 git push的一般形式为 git push <远程主机名> <本地分支名> <远程分支名> ，例如 git push origin master：refs/for/master ，即是将本地的master分支推送到远程主机origin上的对应master分支， origin 是远程主机名。第一个master是本地分支名，第二个master是远程分支名。

- git push origin master
   如果远程分支被省略，如上则表示将本地分支推送到与之存在追踪关系的远程分支（通常两者同名），如果该远程分支不存在，则会被新建
- git push origin ：refs/for/master
   如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支，等同于 git push origin --delete master
- git push origin
   如果当前分支与远程分支存在追踪关系，则本地分支和远程分支都可以省略，将当前分支推送到origin主机的对应分支
- git push
   如果当前分支只有一个远程分支，那么主机名都可以省略，形如 git push，可以使用git branch -r ，查看远程的分支名



#### 新建分支


创建分支的同时切换到该分支上，命令如下：

```
git checkout -b [branch name]
```

git checkout -b [branch name] 的效果相当于以下两步操作：

```
git branch [branch name]
git checkout [branch name]
```
将新分支推送到github
```powershell
git push origin [branch name]
```

``git push origin --delete Chapater6``  可以删除远程分支Chapater6

``git branch -d Chapater8`` 可以删除本地分支（在主分支中）



#### SSH

##### 创建SSH(Mac)

1. 首先运行terminal检查是否已经有SSH Key

```bash
$ cd ~/.ssh
$ ls
```

2. 没有就用```$ ssh-keygen -t rsa -C "your_email@example.com"```创建

   有就用参数`-f`指定key的文件名`id_rsa.github`

```bash
$ ssh-keygen -t rsa -f ~/.ssh/id_rsa.github -C 'your-email'
```

3. 接着又会提示你输入两次密码（该密码是你push文件的时候要输入的密码，而不是github管理者的密码）

   当然，你也可以不输入密码，直接按回车。那么push的时候就不需要输入密码，直接提交到github上了

4. 复制你创建的``id_rsa.pub``或``id_rsa.github``的内容（ssh-rsa开头，邮箱结尾），粘贴到git的setting的ssh中，点击add

5. 如果有两个ssh，需要进行配置，只有一个就可以跳过这一步

   在``.ssh``文件夹中添加``config``文件，内容为

```jsx
Host github.com
    IdentityFile ~/.ssh/id_rsa.github
    User git
```

6. 验证下这个key是不是正常工作，输入：

```bash
$ ssh -T git@github.com
```



##### 创建SSH(windows)

1. 打开本地git bash,使用如下命令生成ssh公钥和私钥对

   `ssh-keygen -t rsa -C 'xxx@xxx.com'` 然后一路回车(-C 参数是你的邮箱地址)

   ![img](https://images2017.cnblogs.com/blog/894443/201712/894443-20171229211426335-267167906.png)

2. 然后打开~/.ssh/id_rsa.pub文件(~表示用户目录，比如我的windows就是C:\Users\Administrator)，复制其中的内容

3. 打开gitlab,找到Profile Settings-->SSH Keys--->Add SSH Key,并把上一步中复制的内容粘贴到Key所对应的文本框，在Title对应的文本框中给这个sshkey设置一个名字，点击Add key按钮

![img](https://images2017.cnblogs.com/blog/894443/201712/894443-20171229211459257-1162181012.png)

　　4. 到此就完成了gitlab配置ssh key的所有步骤，我们就可以愉快的使用ssh协议进行代码的拉取以及提交等操作了

　　5. 再试一下拉取代码和提交代码，应该就不需要输入密码了

###### 本地配置多个ssh key

大多数时候，我们的机器上会有很多的git host,比如公司gitlab、github、oschina等，那我们就需要在本地配置多个ssh key，使得不同的host能使用不同的ssh key ,做法如下（以公司gitlab和github为例）：

1. 为公司生成一对秘钥ssh key

   ```
   ssh-keygen -t rsa -C 'yourEmail@xx.com' -f ~/.ssh/gitlab-rsa
   ```

2. 为github生成一对秘钥ssh key

   ```
   ssh-keygen -t rsa -C 'yourEmail2@xx.com' -f ~/.ssh/github-rsa
   ```

3. 在~/.ssh目录下新建名称为config的文件（无后缀名）。用于配置多个不同的host使用不同的ssh key，内容如下：

   ```
   # gitlab
   Host gitlab.com
       HostName gitlab.com
       PreferredAuthentications publickey
       IdentityFile ~/.ssh/gitlab_id-rsa
   # github
   Host github.com
       HostName github.com
       PreferredAuthentications publickey
       IdentityFile ~/.ssh/github_id-rsa
     
   # 配置文件参数
   # Host : Host可以看作是一个你要识别的模式，对识别的模式，进行配置对应的的主机名和ssh文件
   # HostName : 要登录主机的主机名
   # User : 登录名
   # IdentityFile : 指明上面User对应的identityFile路径
   ```

4. 按照上面的步骤分别往gitlab和github上添加生成的公钥gitlab_id-rsa.pub和github_id-rsa.pub

5. OK，大功告成，再次执行git命令验证是不是已经不需要再次验证权限了。

6. 再次查看~/..ssh目录下的文件,会有gitlab_id-rsa、gitlab_id-rsa.pub和github_id-rsa、github_id-rsa.pub四个文件