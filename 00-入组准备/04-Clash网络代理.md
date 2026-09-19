# Clash：安装与简单使用

[返回入组准备](README.md)

访问 GitHub、论文网站等资源遇到网络问题时，可以使用 Clash 代理。这里以 **Clash Verge Rev** 为例。

## 1. 安装

从[项目发布页](https://github.com/clash-verge-rev/clash-verge-rev/releases/latest)下载正式版，选择对应系统和芯片的安装包：

- **Windows**：一般选 `x64-setup.exe`，ARM 电脑选 `arm64-setup.exe`，下载后按提示安装。
- **macOS**：Apple M 系列选 `aarch64.dmg`，Intel 选 `x64.dmg`。打开后将应用拖入“应用程序”。
- **Linux**：按发行版选择 `.deb` 或 `.rpm`，架构与电脑一致，安装方法见[官方说明](https://www.clashverge.dev/install.html)。

下载页打不开时，找老师或同学协助获取安装包。

## 2. 导入订阅

**订阅码请私聊张鑫老师获取。** 按收到的说明取得订阅链接，不要把订阅码或链接发到公开仓库。

打开客户端的“订阅”页面，粘贴订阅链接并导入，然后选中这份订阅。导入后应能在“代理”页面看到节点列表。

## 3. 开始使用

1. 在“代理”页面选择**规则模式（Rule）**，由订阅规则决定哪些连接走代理。
2. 在相应代理组中选择节点，可先测速，再选一个可用节点。
3. 打开**系统代理**，用浏览器访问 GitHub，确认连接正常。使用期间保持客户端运行。
4. 不用时先关闭系统代理，再退出客户端。

连接失败时，先更新订阅、换一个节点重试。系统代理主要适用于浏览器；终端中的 Git、SSH 不一定自动走代理，需要单独配置，不能仅凭网页能打开判断。

更多操作见[官方快速入门](https://www.clashverge.dev/guide/quickstart.html)。
