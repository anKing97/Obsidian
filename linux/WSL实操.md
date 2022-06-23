# 1、将子系统移动至其他硬盘
1. 首先查看所有 wsl 子系统：
```powershell
wsl -l --all -v
```
2. 导出分发版为 tar 文件到 d 盘：
```powershell
wsl --export Ubuntu-20.04 d:\wsl-ubuntu20.04.tar
```
3. 注销当前分发版：
```powershell
wsl --unregister Ubuntu-20.04
```
4. 重新导入并安装 wsl 在指定的文件夹：
```powershell
wsl --import Ubuntu-20.04 D:\ProgramApp\wsl\Ubuntu-22.04 d:\wsl-ubuntu20.04.tar --version 2
```
5. 设置默认登陆用户为安装时的用户名：
```
ubuntu2004 config --default-user zw
```
6. 删除 tar 文件：
```
del d:\wsl-ubuntu20.04.tar
```
# 2、配置wsl使用主机代理
首先在 `Clash for Windows` 中打开 `allow lan` 按钮，然后鼠标移动到上面会出现指定的 ip 地址：  
![[Pasted image 20220622162802.png]]
此时记住 WSL 的 IP 地址：172.20.0.1，以及配置的端口号：7890  
接着在 WSL 中 输入：`sudo gedit ~/.bashrc` ，然后在末行写入：
```bash
export http_proxy=172.20.0.1:7890
export https_proxy=172.20.0.1:7890
```
到此配置完毕，可以利用 `wget google.com` 进行测试。
# 3、配置 zsh 终端
1. 安装 zsh
`sudo apt install zsh`
2. 设置 zsh 为默认 shell
`chsh -s /bin/zsh`
3. 安装 ohmyzsh，默认下载文件夹为： `~/.oh-my-zsh`
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
4. 安装插件：
```bash
# 语法高亮插件 
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting 
# 自动提示插件 
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions

# 安装 autojump 自动跳转插件
sudo apt install autojump
```
5. 配置 `~/.zshrc` ： `gedit ~/.zshrc` 并搜索 `plugins` ，之后写入所有插件名：
```bash
plugins=(
git
z
extract # 快速解压缩
zsh-autosuggestioins
zsh-syntax-highlighting
autojump
)
```
6. 之后输入 `source ~/zshrc`  让其生效。
# 4、安装 anaconda
直接在 anaconda 官网下载 `.sh` 文件，然后复制到 `/tmp` 文件夹下，接着运行：
```zsh
sh Anaconda3-2022.05-Linux-x86_64.sh
```
或者直接在 `zsh` 中运行：
```zsh
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh

sh Anaconda3-2022.05-Linux-x86_64.sh
```
# 5、配置 GNOME 桌面版 Ubuntu
[Windows中WSL2 配置运行GNOME桌面版 Ubuntu-51CTO.COM](https://os.51cto.com/article/698844.html)


# ==Centos87==
## 1、卸载 Centos7
在 `PowerShell` 中切换到 `Centos7` 的安装目录下，运行：
```powershell
./Centos8.exe clean
```

![[Pasted image 20220623102353.png]]
