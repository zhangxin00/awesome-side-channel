# 第十周：可信执行环境（选读）

[返回首页](../README.md) · [上一周](../09-中断侧信道/README.md) · [下一周](../11-硬件安全与密码学/README.md)

可信执行环境（TEE）保护程序免受部分高权限软件的干扰。不同 TEE 信任的组件不同，本周关注这些假设及其漏洞。

## 本周论文

- [CCS'21] [SmashEx: Smashing SGX Enclaves Using Exceptions](2021-SmashEx.pdf)

- [S&P'24] [WeSee: Using Malicious #VC Interrupts to Break AMD SEV-SNP](2024-WeSee.pdf)

- [SEC'24] [CacheWarp: Software-based Fault Injection using Selective State Reset](2024-CacheWarp.pdf)

- [SEC'26] [UncoreBleed: AEX-Free, High-Resolution, and Low-Noise Side-Channel Attacks on SGX Enclaved Execution](2026-UncoreBleed.pdf)

## 本周任务

为上面的每篇论文写一段英文摘要，另找近 3 年的 5 篇 TEE 侧信道论文，按兴趣排序。摘要与文献清单随周五邮件发送，格式见[邮件示例](../01-如何阅读论文/Email格式.md)。

逐篇写出可信计算基、攻击者特权和被破坏的安全属性。不要把 SGX enclave 与受保护虚拟机的信任边界混为一谈。
