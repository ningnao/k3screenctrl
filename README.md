## 简介

在 [zxlhhyccc/Hill-98-k3screenctrl](https://github.com/zxlhhyccc/Hill-98-k3screenctrl) 已经给K3屏幕开启了7屏的基础上，使用 [K3 openwrt18.06.02](https://www.right.com.cn/forum/thread-466672-1-1.html) 固件中的```/lib/k3screenctrl/```下的sh文件做了替换

搭配的 luci-app 是根据固件的LuCi文件修改的 [lwz322/luci-app-k3screenctrl](https://github.com/lwz322/luci-app-k3screenctrl)

最后使用修改自 [lean/lede](https://github.com/lean/lede) 中的编译文件 [k3screenctrl_build](https://github.com/lwz322/k3screenctrl_build) 编译

其他可以参考：[lanceliao/k3screenctrl](https://github.com/lanceliao/k3screenctrl)

## 屏幕界面
基本情况可以参考下图：

![](https://img.vim-cn.com/19/60fc4e2bff1f25017180216244e1fafe20f608.png)

另外新版本通过修改脚本，添加了更多信息的显示的选项，包括：CPU温度，负载，内存，运行时间等

第一屏：升级界面

第二屏：型号，温度，MAC，软件版本

第三屏：接口

第四屏：网速以及2.4G和5G WiFi的接入客户端数量

第五屏：天气，时间

第六屏：WiFi信息：SSID和密码（可选隐藏）

第七屏：已接入终端和网速（只统计IPv4转发）

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