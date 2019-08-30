## 简介

在 [zxlhhyccc/Hill-98-k3screenctrl](https://github.com/zxlhhyccc/Hill-98-k3screenctrl) 已经给K3屏幕开启了7屏的基础上，使用 [K3 openwrt18.06.02](https://www.right.com.cn/forum/thread-466672-1-1.html) 固件中的```/lib/k3screenctrl/```下的sh文件做了替换

搭配的 luci-app 是根据固件的LuCi文件修改的 [lwz322/luci-app-k3screenctrl](https://github.com/lwz322/luci-app-k3screenctrl)

最后使用修改自 [lean/lede](https://github.com/lean/lede) 中的编译文件[k3screenctrl_build](https://github.com/lwz322/k3screenctrl_build)编译

## En

On the basic of [zxlhhyccc/Hill-98-k3screenctrl](https://github.com/zxlhhyccc/Hill-98-k3screenctrl)，added sh file from [K3 openwrt18.06.02](https://www.right.com.cn/forum/thread-466672-1-1.html)，It works fine with [lwz322/luci-app-k3screenctrl](https://github.com/lwz322/luci-app-k3screenctrl)
[k3screenctrl_build](https://github.com/lwz322/k3screenctrl_build) modified from [lean/lede](https://github.com/lean/lede)