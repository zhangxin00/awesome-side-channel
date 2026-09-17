# 第三周：体系结构基础

[返回首页](../README.md) · [上一周](../02-网络安全基础/README.md) · [下一周](../04-研究团队与文献追踪/README.md)

本周学习缓存、流水线、推测执行、预取和功耗管理，了解它们如何产生侧信道。

## 要弄清的问题

结合讲义与视频，想一想：

1. 同一段程序为什么可能因缓存状态而运行得快或慢？
2. 预测错误的指令结果被撤销后，为什么仍可能留下微架构痕迹？
3. 功耗、能量、频率与经过的时间分别是什么，为什么不能混用？

## 学习材料

- [功耗管理讲义](功耗管理.pdf)：理解工作与空闲状态。
- [Alder Lake 能效材料](Energy%20Efficiency%20Features%20of%20the%20Intel%20Alder%20Lake%20Architecture.pdf)：后续研究具体平台时选读。
- [缓存层次结构与一致性视频](https://www.youtube.com/watch?v=r_ZE1XVT8Ao&list=PLv4ReNnZeDisuXC-FpiUKP0yKN6wI2Af9)和[流水线视频](https://www.youtube.com/watch?v=BVNx3wtJ9vs)：按需补充。

## 本周任务

在 Linux 终端运行 `lscpu`，查看 CPU 型号、架构、核心数和线程数。有条件时对比几台机器。

用 [Spectre](../01-如何阅读论文/2019-Spectre.pdf) 解释：秘密数据怎样改变缓存状态，攻击者又怎样从访问时间推断数据？把理解写进本周邮件。
