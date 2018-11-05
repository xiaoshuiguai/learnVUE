# learnGit



[TOC]



### ssh -key配置

　　在这一步我已经默认你安装好了Git，打开Git，在Git命令行输入

1. #### 检查电脑本机是否有ssh key设置

   **注意:** .ssh是隐藏文件，一般在电脑C/用户/Administrator下面就能够找到。

~~~
cd  ~/.ssh
~~~

2. #### 配置ssh key

　　一般情况下 ，之前没有用过git的同学电脑本机一般不会 有ssh key 的，下面我讲给大家介绍如何配置ssh key进入~路径下，必须保证当前路径在~路径下。

　　在git命令行敲击 //建议写自己真实有效的邮箱地址。**注意：**在敲代码是不要将双引号也敲击进去。

~~~
ssh-keygen -t  rsa -C "xxx.@yyy.zzz" 
~~~

​	

　　然后命令行会出现如下代码：

　　Enter file in which to save the key (/c/Users/xxxx_000/.ssh/id_rsa):       //此时我们什么都不需要操作，直接回车就好。

　　Enter passphrase (empty for no passphrase):            //此时要你输入码（可以为空，直接回车就好，也可以输入你的密码，这个密码在你最后把本地资源推送到github上面的时候回会让你填写密码，此时密码隐藏，你输入进去是看不到的）。

　　Enter same passphrase again:       //再次确认密码（如果你第一次有输入密码，这次就再输一次，如果没有直接回车就行了）。

　　Your identification has been saved in /c/Users/xxxx_000/.ssh/id_rsa.       *//生成的密钥*

　　Your public key has been saved in /c/Users/xxxx_000/.ssh/id_rsa.pub.          //*生成的公钥*

　　The key fingerprint is:

　　e3:51:33:xx:xx:xx:xx:xxx:61:28:83:e2:81 xxxxxx@yy.com

　　*本机已完成ssh key设置，其存放路径为：c:/Users/xxxx_000/.ssh/下。其中xxxx_000为你的用户名。

 3. #### 添加ssh key 到Github上

    　　首先登陆Github,点击右上角的“▼”→Settings→SSH kyes→Add SSH key。
    　　然后在打开c:/Users/xxxx_000/.ssh里面的id_rsa.pub文件，全选复制公钥内容
    　　也可以在git bush中的命令行输入

    ```
    cat ~/.ssh/id_rsa.pub
    ```

    将得到公钥

　　Title自定义，将公钥粘贴到GitHub中Add an SSH key的key输入框，最后“Add Key“

  4. #### 配置账户

     $ git config --global user.name “your_username”       *#设置用户名*

　　$ git config --global user.email “your_registered_github_Email”       *#设置邮箱地址(建议用注册giuhub的邮箱)*

  5. #### 测试ssh keys是否设置成功。

     ssh -T git@github.com

　　The authenticity of host 'github.com (192.30.252.129)' can't be established.

　　RSA key fingerprint is 16:27:xx:xx:xx:xx:xx:4d:eb:df:a6:48.

　　Are you sure you want to continue connecting (yes/no)? yes #确认你是否继续联系，输入yes

　　Warning: Permanently added 'github.com,192.30.252.129' (RSA) to the list of known hosts.

　　Enter passphrase for key '/c/Users/xxxx_000/.ssh/id_rsa':        *#生成ssh kye是密码为空则无此项，若设置有密码则有此项且，输入生成ssh key时设置的密码即可。*

　　Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.        *#出现此句话，说明设置成功。*

　　到这里，git相关的所有配置已经完成，下面我将给大家介绍最常使用的命令

---



### clone已有仓库

　　git clone git@github.com:XXX/yyyy.git //XXX为github的用户名，yyy为仓库名



$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"



git init

git add

git commit -m "版本说明"