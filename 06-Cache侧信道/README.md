# 第六周：Cache 侧信道

[返回首页](../README.md) · [上一周](../05-Prefetcher侧信道/README.md) · [下一周](../07-功耗侧信道/README.md)

缓存命中和未命中的时间不同，攻击者可以据此推断受害者的访问行为。本周学习 Flush+Reload、Prime+Probe 及其扩展。

## 本周论文

- [SEC'14] [FLUSH+RELOAD: a High Resolution, Low Noise, L3 Cache Side-Channel Attack](2014-Flush-Reload.pdf)

- [S&P'15] [Last-Level Cache Side-Channel Attacks are Practical](2015-Last-Level-Cache.pdf)

- [SEC'23] [(M)WAIT for It: Bridging the Gap between Microarchitectural and Architectural Side Channels](2023-MWAIT-for-It.pdf)

- [CCS'24] [Spec-o-Scope: Cache Probing at Cache Speed](2024-Spec-o-Scope.pdf)

## 本周任务

为上面的每篇论文写一段英文摘要，另找近 2 年的 5 篇 Cache 侧信道论文，按兴趣排序。摘要与文献清单随周五邮件发送，格式见[邮件示例](../01-如何阅读论文/Email格式.md)。

阅读 Flush+Reload 原文，比较它与 Prime+Probe 的共享条件。复现前先测受控条件下的时延分布，不直接照抄缓存阈值。
