### 这个工具是用来干嘛的

平日里，我们需要管理多个远程服务器，每次都需要自己记下服务器地址和账户密码。为了简化这个流程，我写了这个简单的小工具来管理远程服务器。

这个小工具在添加服务器的时候，会自动的检测远程服务器于你的本地电脑是否已经做了ssh免密登录，如果没有的话，则会自动把你的ssh公钥上传到服务器上来实现免密登录(当然，你也可以不上传到服务器中，在上传时，你不输入远程服务器的密码即可。只是这样的话，你每次登录服务器都需要手动的去输入密码)


### 如何使用

##### 安装

将此仓库克隆到本地后，进入目录中执行`./init.sh`，然后输入你要安装的位置，init脚本会自动的帮你拷贝ssh-helper.sh脚本到你指定的目录，然后再`/user/local/bin`中增加一个执行新文件的软链接，这样你就可以全局的使用`ssh-helper`这个命令。 


##### 添加服务器:

```bash
ssh-helper -a tag_name root@192.168.0.0.1 
```
> 默认不会创建ssh-key 免密登录，如果需要，则要在host后面添加 `y`
```bash
ssh-helper -a tag_name root@192.168.0.0.1 y
```

8888 就是我们服务器使用的端口号。

##### 删除服务器

```bash
ssh-helper -d tag_name
```

tag_name就是我们刚刚添加时候的tag_name

##### 连接服务器

```bash
ssh-helper -s tag_name
```

##### 列举出服务器列表

有时候你忘记了服务器的tag_name，就可以用下面的命令来列出服务器列表
```bash
ssh-helper -l
```


##### 获取帮助

如果要查看usage的话，可以不带任何参数或者是-h选项。


