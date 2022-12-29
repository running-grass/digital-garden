一款开源的CPU指令集

RISC-V 必须提供三种工作模式，即 Machine Mode, Supervisor Mode 和 User Mode。Supervisor 和 User 分别用于运行我们常见的 Linux 与[用户态](https://www.zhihu.com/search?q=%E7%94%A8%E6%88%B7%E6%80%81&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22509845102%22%7D)应用程序。而 Machine Mode 则用于运行 Bootloader 并装载和执行 OS。

![](https://pic3.zhimg.com/v2-854312b2f16a019b6fb789db303dd5ea_b.jpg)
启动流程：ZSBL-->FSBL-->OpenSBI-->u-boot-->linux
ZSBL和FSBL通常固化在芯片内部，不在本文讨论范围，本文关注OpenSBI。