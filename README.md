## 简介

在 [zxlhhyccc/Hill-98-k3screenctrl](https://github.com/zxlhhyccc/Hill-98-k3screenctrl) 已经给K3屏幕开启了7屏的基础上，使用 [K3 openwrt18.06.02](https://www.right.com.cn/forum/thread-466672-1-1.html) 固件中的```/lib/k3screenctrl/```下的sh文件做了替换（这部分可以自行定制，但是有显示内容的限制）

搭配的 luci-app 是根据固件的LuCi文件修改的 [lwz322/luci-app-k3screenctrl](https://github.com/lwz322/luci-app-k3screenctrl)

最后使用修改自 [lean/lede](https://github.com/lean/lede) 中的编译文件 [k3screenctrl_build](https://github.com/lwz322/k3screenctrl_build) 编译

其他的有效信息可以参考：[lanceliao/k3screenctrl](https://github.com/lanceliao/k3screenctrl)

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
- 天气API有访问频率限额，不过现在用的人太多了，偶尔天气无法查询，如果有需求可以自行申请API；脚本中使用的天气API来自[心知天气](https://www.seniverse.com/)，手机号即可申请免费版，得到私钥后，于`/lib/k3screenctrl/weather.sh`中替换`smtq3n0ixdggurox`
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