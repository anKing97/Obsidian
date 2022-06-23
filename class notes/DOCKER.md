# DOCKER

Created: April 4, 2022 9:59 AM
Reviewed: No
Type: 不知道是什么的东西
状态: 待学习

# 一、DOCKER的安装

首先需要解决 **Window10家庭版** 的问题，主要是家庭版没有 **Hyper-V**。这里利用代码安装。

新建 `.txt` 文件，然后复制代码进去，最后改为 `.cmd` 文件，然后用管理员身份运行。

```python
pushd "%~dp0"
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
del hyper-v.txt
Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL
```

这里会自动安装 **Hyper-V** 服务。

1. **第一个坑  BIOS Hyper-V 未启动：**
    
    在管理员模式的 cmd 中执行如下命令，然后重启电脑
    
    `bcdedit /set hypervisorlaunchtype auto`
    
2. **wsl 2 installation is incomplete. windows 10：**
    
    主要是 wsl 的版本太旧了，还是在管理员模式的 cmd 中执行：
    
    `wsl --update`
    

参考安装文章：

[Win10家庭中文版安装Docker Desktop（亲测成功，建议收藏）_莫小兮丶的博客-CSDN博客](https://blog.csdn.net/qq_45590494/article/details/114760564)

# 二、DOCKER学习

[(32条消息) Docker详解_jeffery0207的博客-CSDN博客_docker详解](https://www.notion.so/32-Docker-_jeffery0207-CSDN-_docker-ddef6fdf1c1d41b0b4727d65f4c96f6e)

[Docker详解_jeffery0207的博客-CSDN博客_docker详解](https://blog.csdn.net/jeffery0207/article/details/85560667?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164904131016780265416839%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164904131016780265416839&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-85560667.142^v5^pc_search_result_control_group,157^v4^control&utm_term=doker%E8%AF%A6%E8%A7%A3&spm=1018.2226.3001.4187)