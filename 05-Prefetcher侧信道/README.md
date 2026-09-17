# 第五周：Prefetcher 侧信道

[返回首页](../README.md) · [上一周](../04-研究团队与文献追踪/README.md) · [下一周](../06-Cache侧信道/README.md)

预取器根据访问历史预测后续访问，提前把数据或指令放入缓存。本周看攻击者如何利用这种预测行为获取信息。

## 本周论文

- [ASPLOS'23] [AfterImage: Leaking Control Flow Data and Tracking Load Operations via the Hardware Prefetcher](2023-AfterImage.pdf)

- [SEC'23] [BunnyHop: Exploiting the Instruction Prefetcher](2023-BunnyHop.pdf)

- [HPCA'24] [PrefetchX: Cross-Core Cache-Agnostic Prefetcher-Based Side-Channel Attacks](2024-PrefetchX.pdf)

## 本周任务

为上面的每篇论文写一段英文摘要，另找近 2 年的 5 篇预取器侧信道论文，按兴趣排序。摘要与文献清单随周五邮件发送，格式见[邮件示例](../01-如何阅读论文/Email格式.md)。

阅读时比较三篇论文的预取对象、训练方法和观测方式。
