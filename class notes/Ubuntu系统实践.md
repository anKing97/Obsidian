# Ubuntu系统实践

Class: 操作系统
Created: May 14, 2022 3:06 PM
Reviewed: No

# 1、软件安装

[Linux玩家必备：Ubuntu完全配置指南](https://zhuanlan.zhihu.com/p/56253982)

## 1.1、安装Docker

[Ubuntu Docker 安装](https://www.runoob.com/docker/ubuntu-docker-install.html)

### **卸载旧版本**：

首先需要卸载 Docker 的旧版本， `docker` ， `[docker.io](http://docker.io)` 和  `docker-engine` 。

```bash
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

### **设置存储库：**

1、更新 `apt` 包索引并且安装包允许 `apt` 通过 HTTPS 使用存储库：

```bash
$ sudo apt-get update

$ sudo apt-get install \
	ca-certificates \
	curl \
	gnupg \
	lsb-release
```

2、添加 Docker 的官方 GPG 密钥：

```bash
$ curl -fsSl https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -
```

3、设置稳定的存储库：

```bash
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable nightly" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 安装 Docker 引擎

安装最新版的 `Docker Engine` 、 `containerd` 和 `Docker Compose` 

```bash
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

### 卸载 Docker 引擎

1、卸载 `Docker Engine` 、 `CLI` `containerd` 和 `Docker Compose`:

```bash
$ sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

2、主机上的映像、容器、卷或自定义配置文件不会自动删除。要删除所有映像、容器和卷：

```bash
$ sudo rm -rf /var/lib/docker
$ sudo rm -rf /var/lib/containerd
```

## 1.2、安装 wine （运行原生的windows应用）

首先安装依赖：

```bash
$ sudo apt install wine
$ sudo apt install winetricks
```

然后执行 `winetricks` 来修复 bug

```bash
$ winetricks riched20
```

此方法相当于在 ubuntu 中运行 Windows 子系统，想要安装 QQ 或者 微信，只需在官网下载 `.exe` 安装包，然后执行：

```bash
$ wine WeChatSetup.exe
```

具体应用的列表可以在 `.wine/drive_c/Program Files(x86)/` 中查看，比如安装的 微信： `.wine/drive_c/Program Files(x86)/Tencent/WeChat`

## 1.3、安装搜狗输入法

首先在搜狗输入法官网 `https://pinyin.sougou.com/linux/` 下载 linux 版本的输入法 `.deb` 文件，然后安装：

```bash
$ sudo dpkg -i sogoupinyin_4.0.1.2123_amd64.deb
# 安装相关的依赖
$ sudo apt-get install -f
```

接下来需要更新 linux 的软件仓库：

```bash
$ sudo add-apt-repository ppa:fcitx-team/nightly
$ sudo apt-get update

# 接下来安装依赖包：
$ sudo apt install libqt5qml5 libqt5quick5 libqt5quickwidgets5 qml-module-qtquick2
$ sudo apt install libgsettings-qt1
```

接下来在 `language supporting` 中将 `keyboard input method system:` 改为 `fcitx` 。最后配置文件，讲 `sougoupinyin` 加入列表。

## 1.4、安装Typora

ubuntu 可以安装最后一个不收费版本的 Typora：直接在 `release` 界面找：

[Typora - macOS release channel](https://www.typora.io/releases/all)

## 1.5、安装QQ

目前比较好用的一个QQ版本是 `github` 上面的:

[GitHub - Icalingua-plus-plus/Icalingua-plus-plus: A client for QQ and more.](https://github.com/Icalingua-plus-plus/Icalingua-plus-plus)

![Untitled](Untitled%2011.png)

目前其他版本的QQ可以向 linux 上面传文件，但是 linux 上面不能往外边传

# 2、系统配置

## 2.1、配置连接校园网：

针对于深澜系统，通过 `DSL` 连接西北工业大学校园网：

```bash
$ nmcli con edit type pppoe con-name "校园网"

$ set pppoe.username 用户名
$ set pppoe.password 密码
```

用户名和密码输入完成之后，继续输入 `save` ， 然后 `quit` 。之后，网络连接中就会出现以 校园网 命名的 `DSL` `PPPOE` 网络连接。

然后在网络设置中，将连接的上级接口改为 `ens4` 

**删除某一网络连接：**

直接在 高级网络配置 中进行更改。

## 2.2、配置 FTP 服务器

这里选择 `vsftpd` 为 ubuntu 上的服务器，首先先下载软件：

```bash
$ sudo apt-get install vsftpd
```

然后创建用户并配置密码：

```bash
$ sudo useradd -m ftp用户名
$ sudo passwd ftp用户名
New password:
Retype new password:
passwd:password update successfully
```

此步之后，会在 `/home` 路径内创建一个 `ftp用户名` 的文件夹，接着，修改文件夹的权限：

```bash
$ sudo chmod -R 777 /home/ftp用户名
```

然后修改配置文件：

```bash
$ sudo gedit /etc/vsftpd.conf
```

将其修改为：

```bash
listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
pasv_enable=Yes
pasv_min_port=10000
pasv_max_port=10100
allow_writeable_chroot=YES
local_root=/home/ftp用户名
```

随后重启 ftp 服务器：

```bash

$ sudo service vsftpd restart
```

至此，就可以在其他电脑上访问ubuntu机器上的 ftp 服务器了。

> 注：两台电脑必须处于同一个局域网内，比如校园网，不可以在校园网范围外访问校园网内的服务器。
> 

另外，还可以设置多个用户，这时，需要创建一个 `userlist_file` ，用来存储所有创建的用户名，不在 `userlist_file` 内的用户即使同处于一个局域网内，也无法访问服务器。同样在 `/etc/vsftpd.conf` 内配置文件：

```bash
userlist_deny=NO
userlist_file=/etc/allowed_users
seccomp_sandbox=NO
local_root=/home/ftp用户名
```

在增加了ftp用户之后，只需要在 `/etc/allowed_users` 文件内写入新增加的用户名。

# 3、问题记录

## 3.1、有线网络问题

ubuntu 有线网不停的重复连接，首先是 `/etc/network/interfaces` 配置文件出错，正常情况下不需要进行修改，原文件内容为：

```bash
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

如果没有特殊原因，应该保持上面的配置文件为原样。

## 3.2、U盘启动盘有写保护问题：

在装完 Ubuntu 之后，启动盘格式化的时候，会出现u盘有写保护，无法格式化，此时，可以进行如下操作，去除写保护：

1. 按 `win` + `R` ，并在其中输入 `diskpart` 。
2. 输入 `list disk` ，列出所有的磁盘，然后选择需要去除写保护的磁盘：
    
    [https://www.notion.so](https://www.notion.so)
    
3. 比如 1 号磁盘为目标磁盘。然后输入 `select disk 1` 。
4. 接下来输入 `attributes disk clear readonly` ，这一命令可以清楚磁盘的写保护状态。
5. 接下来输入 `clean` 可以清楚 u 盘内的所有数据，然后输入 `exit` 退出命令框。
6. 接下来在 文件资源管理器中直接将 u 盘进行格式化即可。