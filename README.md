# precision_report_rate
一个精确测试HID报告率的软件

Windows 普通的计时器只能精确到1ms(毫秒), 报告率超过1000HZ即无法正确统计，再加上Windows系统及软件的时间损耗，误差很大。

实现方式：

软件通过给USB或HID 类别的设备加载一个低级别过滤驱动（lowwer level filter driver)，
在驱动中计算设备上传数据的报告率（如游戏鼠标的报告率）。

使用硬件级1us(1微秒，1ms= 1000us)的精确统计函数：

KeQueryPerformanceCounter 
QueryPerformanceFrequency 

https://docs.microsoft.com/en-us/windows-hardware/drivers/ddi/ntifs/nf-ntifs-kequeryperformancecounter
https://docs.microsoft.com/en-us/windows/win32/api/profileapi/nf-profileapi-queryperformancefrequency

开源软件包含两部分：
1、busdog2 USB & HID BUS LOWWER FILTER DRIVER (类似bushound功能）
2、PRR_GUI(用于显示统计数据）

其它部分：

WINDOWS 驱动程序自签名技术，请上如下网站查看：

https://www.whqlchina.com

安信实验室技术研发中心
