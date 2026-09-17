# SSH：做实验与远程工作（含北大 VPN）

[返回入组准备](README.md) · [上一节：Zotero 看论文](01-Zotero看论文.md) · [下一节：LaTeX 写论文](03-LaTeX写论文.md)

SSH 用来远程登录实验室服务器。以下示例中的用户名、地址和端口要换成管理员提供的信息。

## 1. 准备账号与连接信息

向管理员确认服务器地址、端口、账号、登录方式和主机公钥指纹，以及是否需要 VPN 或跳板机。顺便问清工作目录和设备使用规则。VPN 和服务器的账号可能不同。

下文的“本地”指自己的电脑，“远程”指服务器。拿不准时用 `hostname` 和 `pwd` 查看机器和目录。密码、私钥不要放进代码仓库。

## 2. 北大 VPN

连接北大内网需要有访问资格的校园网账号；其他同学使用所在单位的 VPN。

| 需求 | 入口或方式 | 说明 |
| --- | --- | --- |
| 校外用本机终端连接北大内网服务器 | 客户端内网模式：`https://pacvpn.pku.edu.cn` | 校园内网业务经 VPN，其他资源走本地网络 |
| 以校园网身份访问图书馆等互联网资源 | 客户端全业务模式：`https://vpn.pku.edu.cn` | 具体文献仍受资源授权限制 |
| 只访问校内网页 | 官方服务页中的浏览器入口 | Web VPN 仅覆盖部分网页；WPN 另提供浏览器内 SSH 等功能 |

安装包和入口见[北大 VPN 安装说明](https://its.pku.edu.cn/service_1_vpn_client.jsp)与[服务总览](https://its.pku.edu.cn/service_1_vpn_readme.jsp)。浏览器里的 WPN 终端不会让本机 `ssh` 自动连上内网。

### 安装与连接

1. 打开官方安装页，按操作系统、版本和 CPU 架构选择客户端。Windows、macOS、Linux 安装包均从该页面获取；名称可能显示为 Pulse Secure 或 Ivanti Secure Access Client。
2. 安装后新建连接，名称可写“北大内网”或“北大全业务”，服务器地址按上表填写。
3. 选择连接，输入本人账号密码，完成界面要求的认证。
4. 连接成功后，在本机终端运行后面的 SSH 命令。
5. 工作结束后断开 VPN。需要保留远程任务时，参见第 6 节。

校内是否需要 VPN，按管理员说明操作。

### VPN 故障定位

连不上时，依次检查本地网络、VPN 状态、连接模式和目标地址。代理或其他 VPN 可能造成冲突。VPN 认证失败查校园账号，SSH 认证失败查服务器账号。

求助时附上系统版本、连接模式、目标地址和完整报错。常见问题见[安装页](https://its.pku.edu.cn/service_1_vpn_client.jsp)。

## 3. 第一次 SSH 登录

Windows 使用 PowerShell 或 Windows Terminal；macOS、Linux 使用终端。在**本地**检查：

```sh
ssh -V
```

Windows 若找不到命令，在“可选功能”中安装 **OpenSSH 客户端**，参考[微软官方说明](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)。连接 Linux 服务器不需要在自己电脑开启 SSH 服务。macOS 通常自带客户端；Linux 缺少客户端时使用发行版的软件包管理工具安装。

在**本地**执行，示例使用 22 端口：

```sh
ssh -p 22 student@server.example.org
```

首次连接显示服务器公钥指纹，通过管理员提供的可信渠道核对后再输入 `yes`。输入服务器密码时终端通常不显示字符或星号，这是正常现象。

登录成功后，在**远程**执行：

```sh
whoami
hostname
pwd
mkdir -p ~/side-channel-learning
cd ~/side-channel-learning
printf 'hello from the lab\n' > hello.txt
cat hello.txt
exit
```

`exit` 返回本地。SSH 参数说明见 [OpenSSH 手册](https://man.openbsd.org/ssh)。

## 4. 密钥登录与连接别名

在**本地**创建独立密钥：

```sh
ssh-keygen -t ed25519 -C "your-name-lab" -f ~/.ssh/id_ed25519_lab
```

按提示设置口令，同名密钥已存在时不要覆盖。`id_ed25519_lab` 是私钥，自己保管；`id_ed25519_lab.pub` 是公钥，可以交给管理员。参数见 [ssh-keygen 手册](https://man.openbsd.org/ssh-keygen)。

macOS/Linux 查看公钥：

```sh
cat ~/.ssh/id_ed25519_lab.pub
```

Windows PowerShell 查看公钥：

```powershell
Get-Content $HOME/.ssh/id_ed25519_lab.pub
```

将公钥完整一行交给管理员，安装到本人远程账号的 `~/.ssh/authorized_keys`。若允许自行安装且已能密码登录，在有 `ssh-copy-id` 的 macOS/Linux 上可运行：

```sh
ssh-copy-id -i ~/.ssh/id_ed25519_lab.pub -p 22 student@server.example.org
```

也可以请管理员安装公钥。另开终端测试登录，成功前保留原会话。

编辑**本地** `~/.ssh/config`；Windows 对应用户目录的 `.ssh/config`，注意不是 `config.txt`。将以下块加入已有文件，不覆盖其他连接：

```sshconfig
Host lab
    HostName server.example.org
    User student
    Port 22
    IdentityFile ~/.ssh/id_ed25519_lab
    IdentitiesOnly yes
    ServerAliveInterval 30
    ServerAliveCountMax 3
```

以后运行 `ssh lab`。保活参数有助于发现断线，不保证程序持续运行。配置依据 [ssh_config 手册](https://man.openbsd.org/ssh_config)。macOS/Linux 如遇权限问题，本地 `.ssh` 目录应仅本人可访问（`700`），私钥与配置文件仅本人可读写（`600`）。

如管理员要求跳板机，再增加以下块，并在 `Host lab` 块中添加 `ProxyJump lab-jump`：

```sshconfig
Host lab-jump
    HostName jump.example.org
    User student
    Port 22
    IdentityFile ~/.ssh/id_ed25519_lab
    IdentitiesOnly yes
```

跳板机账号和公钥按管理员要求配置，需要 VPN 时先连接 VPN。

## 5. 上传与下载

以下均在**本地**运行，并假定已经配置 `lab` 别名：

```sh
# 上传当前目录中的文件
scp ./notes.md lab:~/side-channel-learning/

# 下载前面创建的文件
scp lab:~/side-channel-learning/hello.txt ./hello-from-server.txt

# 上传目录，先确认不含密码或私钥
scp -r ./experiment lab:~/side-channel-learning/
```

路径含空格时加引号。上传前需自行准备示例中的 `notes.md` 或 `experiment` 目录。`scp` 可能覆盖目标同名文件，结果应按日期或实验编号保存。不使用别名时，指定端口使用大写 `-P`，而 `ssh` 使用小写 `-p`，见 [scp 手册](https://man.openbsd.org/scp)。

## 6. 断线后继续工作

在允许交互实验且已安装 `tmux` 的**远程实验节点**执行：

```sh
tmux new -s learning
```

在会话内运行程序。按 `Ctrl-b`，松开后按 `d`，离开会话但保持它运行。重新 SSH 登录后执行：

```sh
tmux ls
tmux attach -t learning
```

会话内输入 `exit` 关闭当前 shell。服务器重启、资源回收或作业超时仍会终止任务。有调度系统时，长任务按管理员要求提交；登录节点只做编辑与轻量检查。

## 7. 常见 SSH 报错

| 报错或现象 | 优先检查 |
| --- | --- |
| `Could not resolve hostname` | 拼写、VPN 的 DNS，是否误在 SSH 主机名前加了 `https://` |
| `Connection timed out` / `No route to host` | VPN、地址、路由、防火墙、跳板机；不是密码错误 |
| `Connection refused` | 端口是否正确，SSH 服务是否启动，由管理员确认 |
| `Permission denied` | 用户名、公钥登记、所选密钥及账号权限 |
| `REMOTE HOST IDENTIFICATION HAS CHANGED` | 先核实是否重装或更换服务器，不要直接关闭主机校验 |
| `Too many authentication failures` | 指定正确 `IdentityFile`，设置 `IdentitiesOnly yes` |
| 无权写文件 | 用 `pwd` 检查路径，回到本人工作目录，并检查配额 |

在本地运行 `ssh -v lab` 可查看诊断信息，分享前检查个人信息。`ping` 失败不能单独证明服务器不可达，因为网络可能禁止 ICMP。

试一次完整流程：登录服务器，上传和下载文件，再从 `tmux` 分离并重新连接。完成后进入 [LaTeX：写论文](03-LaTeX写论文.md)。
