## 简介

在 [zxlhhyccc/Hill-98-k3screenctrl](https://github.com/zxlhhyccc/Hill-98-k3screenctrl) 已经给K3屏幕开启了7屏的基础上，使用 [K3 openwrt18.06.02](https://www.right.com.cn/forum/thread-466672-1-1.html) 固件中的```/lib/k3screenctrl/```下的sh文件做了替换（这部分可以自行定制，但是有显示内容的限制）

搭配的 luci-app 是根据固件的LuCi文件修改的 [lwz322/luci-app-k3screenctrl](https://github.com/lwz322/luci-app-k3screenctrl)

最后使用修改自 [lean/lede](https://github.com/lean/lede) 中的编译文件 [k3screenctrl_build](https://github.com/lwz322/k3screenctrl_build) 编译

其他的有效信息可以参考：[lanceliao/k3screenctrl](https://github.com/lanceliao/k3screenctrl)

**2020.1.31 天气API的问题**：[已知的一个致命问题](https://www.right.com.cn/forum/thread-2068254-1-1.html)
> 屏幕会隔三差五的睡死，睡死时候，网路会出异常，变得非常慢，检查系统日志，会发现k3screenctrl大量的错误信息。硬重启后恢复正常。软重启无法激活屏幕。
> 所有带k3screenctrl的固件都有睡死问题，据说是天气API导致的。但是也有人说一切正常，所以真实原因，自己刷了才知道

考虑到作为路由器还是要稳定性优先的，所以尽可能排除不稳定因素，参考了下[ K3 OpenWrt固件（更新日期 2020.1.30）](https://www.right.com.cn/forum/thread-2512521-1-1.html)，决定本仓库的代码默认不再自带天气的私钥，默认不再开启天气更新（更新间隔设置为0，脚本不运行），有需求可以自行申请[心知天气](https://www.seniverse.com/)的API或者下载已经提供了API Key的固件；

## 屏幕界面
基本情况可以参考下图：

![](https://img.vim-cn.com/f7/53d38adeae90d86c1c94e757ecf18a872af9bc.png)

- 第一屏：升级界面
- 第二屏：型号(硬件版本型号H/W全部显示为A1)，MAC，软件版本
- 第三屏：USB与网口接入情况
- 第四屏：网速以及2.4G和5G WiFi的接入客户端数量
- 第五屏：天气，时间
- 第六屏：WiFi信息：SSID和密码（可选隐藏）
- 第七屏：已接入终端和网速（只统计IPv4转发）

上面主要是接近官方固件的屏幕信息显示，针对新版本通过修改脚本，添加了在前两屏更多信息的显示的选项，默认开启，如下

![](https://img.vim-cn.com/91/4a753ea2b240b547f2a2ee2a62697e27433c62.png)

- **U:0.14 R:8%**：CPU负载 内存占用百分比（和第二屏的软件版本显示的一样）
- **up 10:47**：运行时间
- **H/W: 48*C**：CPU温度
- **MAC地址: OpenWrt 19.07.0**：系统版本号

## 已知问题

- 部分设备的屏幕在使用本软件后无法正常显示界面，可能是屏幕本身的固件版本较低
- 依靠IP定位偶尔可能无法定位到准确的城市，进而无法自动查询天气，建议关闭IP定位，指定城市即可
- WiFi信息部分的访客网络信息，OpenWrt官方没有访客网络的APP，也就没有标准一说，脚本中的设置貌似不适合添加SSID访客网络的做法
- 在开启硬件转发加速（HWNAT或者offload）的情况下，iptable无法统计流量

## En

On the basic of [zxlhhyccc/Hill-98-k3screenctrl](https://github.com/zxlhhyccc/Hill-98-k3screenctrl)，added .sh file from [K3 openwrt18.06.02](https://www.right.com.cn/forum/thread-466672-1-1.html)，It works fine with [lwz322/luci-app-k3screenctrl](https://github.com/lwz322/luci-app-k3screenctrl) &
[k3screenctrl_build](https://github.com/lwz322/k3screenctrl_build) (from[lean/lede](https://github.com/lean/lede))

## Screen Interface
New Version add additional info display, including: CPU temprature, Load, RAM, uptime, etc

1. Update
2. Model, Version, CPU Temp, MAC
3. Port
4. Speed, WiFi (2.4G/5G client) Assicated
5. Weather, Date and Time
6. WiFi Info:SSID & Password (suppressible)
7. Client speed (IPv4 Forward only)