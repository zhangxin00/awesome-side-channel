# 第八周：Spectre 及变体

[返回首页](../README.md) · [上一周](../07-功耗侧信道/README.md) · [下一周](../09-中断侧信道/README.md)

Spectre 利用错误推测执行受害者中的特定代码，再通过缓存等通道泄漏数据。阅读时注意攻击需要什么代码、硬件和训练条件。

## 本周论文

- [S&P'19] [Spectre Attacks: Exploiting Speculative Execution](2019-Spectre.pdf)

- [SEC'23] [Ultimate SLH: Taking Speculative Load Hardening to the Next Level](2023-Ultimate-SLH.pdf)

- [S&P'26] [VMScape: Exposing and Exploiting Incomplete Branch Predictor Isolation in Cloud Environments](2026-VMScape.pdf)

## 本周任务

为上面的每篇论文写一段英文摘要，另找近 2 年的 3 篇 Spectre 或瞬态执行攻击论文，按兴趣排序。摘要与文献清单随周五邮件发送，格式见[邮件示例](../01-如何阅读论文/Email格式.md)。

比较不同变体使用的预测器、瞬态执行路径、泄漏通道和防御方法。

## 补充论文

- [SpecHammer: Combining Spectre and Rowhammer for New Speculative Attacks](2022-SpecHammer.pdf)
- [iLeakage: Browser-based Timerless Speculative Execution Attacks on Apple Devices](2023-iLeakage.pdf)
- [SysBumps: Exploiting Speculative Execution in System Calls for Breaking KASLR in macOS for Apple Silicon](2024-SysBumps-artifact-draft.pdf)（匿名草稿）

本地 SysBumps PDF 是实验包中的匿名草稿，引用以 [CCS 2024 正式记录](https://doi.org/10.1145/3658644.3690189)为准。
