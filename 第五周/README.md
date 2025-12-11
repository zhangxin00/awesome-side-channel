# 功耗侧信道

作为最早的侧信道之一，最初的功耗侧信道使用物理设备监听电源线的电压/电流波动，进而恢复密码芯片中使用的密钥。随着体系结构和侧信道攻击发展，越来越多的功耗管理优化技术被提出，程序间的相互作用导致许多可被观测的信号（architectural hints）出现，进而导致了一系列远程侧信道攻击的发生。

本周，你需要阅读以下几篇文章，并自行搜索本年度发表的三篇可归类为（远程）功耗侧信道的文章。

[S&P'21] PLATYPUS: Software-based Power Side-Channel Attacks on x86

[SEC'22] Hertzbleed: Turning Power Side-Channel Attacks Into Remote Timing Attacks on x86

[XXX] TimeGaps Channels: Exploiting CPU Halted Time for Fun and Profit