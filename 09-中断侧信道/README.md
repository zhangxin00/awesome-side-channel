# 第九周：中断侧信道

[返回首页](../README.md) · [上一周](../08-Spectre及变体/README.md) · [下一周](../10-可信执行环境/README.md)

中断处理会改变处理器状态。这些变化可以暴露按键、程序执行等活动，本周学习如何观测和利用它们。

## 本周论文

- [ESORICS'23] [Indirect Meltdown: Building Novel Side-Channel Attacks from Transient-Execution Attacks](2023-Indirect-Meltdown.pdf)

- [NDSS'24] [IdleLeak: Exploiting Idle State Side Effects for Information Leakage](2024-IdleLeak.pdf)

- [CCS'24] [Cross-Core Interrupt Detection: Exploiting User and Virtualized IPIs](2024-Cross-Core-Interrupt-Detection.pdf)

- [HPCA'24] [SegScope: Probing Fine-grained Interrupts via Architectural Footprints](2024-SegScope.pdf)

## 本周任务

为上面的每篇论文写一段英文摘要，另找近 3 年的 3 篇中断侧信道论文，按兴趣排序。摘要与文献清单随周五邮件发送，格式见[邮件示例](../01-如何阅读论文/Email格式.md)。

为每篇论文记录中断来源、攻击者观察到的状态、时间或空间粒度。说明检测到一次中断与恢复用户秘密之间还缺哪些步骤。
