# WSL报错合集
## WSL报错: Wsl/Service/CreateInstance/CreateVm/HCS/HCS_E_HYPERV_NOT_INSTALLED

参考：[https://learn.microsoft.com/en-us/answers/questions/1336873/how-to-solve-wsl-service-createinstance-createvm-h](https://learn.microsoft.com/en-us/answers/questions/1336873/how-to-solve-wsl-service-createinstance-createvm-h)
### 解决方法

1. 禁用Hyper-V -> 重启
2. 启用Hyper-V -> 重启

## 开着Clash for Windows，报错wsl: 检测到 localhost 代理配置，但未镜像到 WSL。NAT 模式下的 WSL 不支持 localhost 代理。

参考：[https://learn.microsoft.com/en-us/answers/questions/1425728/wsl-localhost-wsl-nat-wsl-localhost](https://learn.microsoft.com/en-us/answers/questions/1425728/wsl-localhost-wsl-nat-wsl-localhost)
### 解决方法

1. 在 C:\Users\<your_username> 中创建一个名为“.wslconfig”的新文件。
将以下内容写入文件：
```yaml
[experimental]
autoMemoryReclaim=gradual  
networkingMode=mirrored
dnsTunneling=true
firewall=true
autoProxy=true
```

2. 在退出wsl的前提下，运行`wsl --shutdown`

# WSL配置图形化界面

> 注意：
> 仅支持WSL2。

我是按照这篇[教程](https://www.bilibili.com/read/cv11143517/)来进行配置的，只不过ip我用的是评论区的`localhost`，~~主要还是分不清各种ip地址。~~ 
所需工具：[VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv/)

由于我们用的是轻量级桌面可能不太“炫酷”，所以就需要我们自己来美化啦。
推荐下面几个网址：
- [https://www.xfce-look.org/browse/](https://www.xfce-look.org/browse/)
# WSL卸载操作

>虽然 Linux 发行版可以通过 Microsoft Store 安装，但不能通过 Microsoft Store 卸载。
>可以通过下列命令卸载。

1. 查看当前环境安装的wsl

```bash
wsl --list
```

2. 注销（卸载）当前安装的Linux的Windows子系统

```bash
wsl --unregister Ubuntu
```

3. 卸载成功，查看当前安装的Linux的Windows子系统

```bash
wsl --list
```

4. 查看可安装的Linux的Windows子系统

```bash
wsl --list --online
```

>说明:
>用WSL注销发行版，以便可以重新安装或清理它。
>注意：一旦取消注册，与该发行版相关的所有数据、设置和软件都将永久丢失。如果需要可以从商店重新安装将>安装分发的干净副本。
