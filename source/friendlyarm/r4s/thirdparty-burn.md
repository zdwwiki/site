---
title: R4S第三方固件
date: 2021-05-30 15:23:23
---





# SuLingGG

SuLingGG大的github地址: 

[SuLingGG/OpenWrt-Mini: Customized Pure OpenWrt & Self-Build OpenWrt Packages Project. (github.com)](https://github.com/SuLingGG/OpenWrt-Mini)

[SuLingGG/OpenWrt-Rpi: Raspberry Pi & NanoPi R2S/R4S & G-Dock & x86 OpenWrt Compile Project. (Based on Github Action / Daily Update)](https://github.com/SuLingGG/OpenWrt-Rpi)

分普通包和精简包

本文以精简固件包为例

## 1. 固件包下载

精简固件包：https://openwrt.cc/snapshots/targets/rockchip/armv8/

R4S建议采用immortalwrt-rockchip-armv8-friendlyarm_nanopi-r4s-ext4-sysupgrade.img.gz.



普通固件包：https://openwrt.cc/releases/targets/rockchip/armv8/

R4S建议采用openwrt-rockchip-armv8-friendlyarm_nanopi-r4s-ext4-sysupgrade.img.gz.



下载对应的固件包，使用Etcher等工具写入到TF卡，然后把TF卡插入到R4S，插好网线后，通电启动。



## 2. 配置

### 网络配置

配置WAN和LAN口。默认LAN口IP是192.168.1.1。

#### 配置IPv6

用工具ssh进入，或直接用TTYD，输入 `ipv6-helper install`，按提示最后重启即可。

IPv6部分命令：

```
ipv6-helper install: 安装 IPV6 模块并将 IPV6 配置为服务器 (Server) 模式 (默认)
ipv6-helper remove: 移除 IPV6 模块并回滚与 IPV6 相关的所有配置

额外用法
ipv6-helper server: 将 IPV6 配置为服务器 (Server) 模式
ipv6-helper relay: 将 IPV6 配置为中继 (Relay) 模式
ipv6-helper hybird: 将 IPV6 配置为混合 (Hybird) 模式
ipv6-helper clean : 移除与 wan3 相关的模块和 LuCI APP (不可逆/一般用不到)
```

### 测试网速（可选）

```
openssl speed -evp aes-256-gcm
openssl speed -evp chacha20-poly1305
/etc/coremark.sh
```

### 磁盘扩容

### 无线配置（可选）

```
opkg update
opkg install hostapd
opkg install wpa-supplicant
```

## 3. 安装应用

该固件可安装的应用列表

https://github.com/SuLingGG/OpenWrt-Mini/blob/main/doc/LuCI-App-List.md

### 安装指南

更新软件包索引:

```
opkg update
```

列出可安装的所有 LuCI APP :

```
opkg list | grep luci-app | grep -v Translation
```

安装软件包 (以 luci-app-ssr-plus 为例):

```
opkg install luci-app-ssr-plus
```

若发现此时新安装软件包界面为英文，则尝试查找该软件包的中文翻译包:

```
opkg list | grep luci-app-ssr-plus | grep zh-cn
```

此时可以得到该软件包的中文翻译包为 `luci-i18n-ssr-plus-zh-cn`，使用 `opkg install` 命令安装此翻译包即可:

```
opkg install luci-i18n-ssr-plus-zh-cn
```

### 建议安装的应用

```
opkg update

opkg install luci-app-ssr-plus
opkg install luci-i18n-ssr-plus-zh-cn

opkg install luci-app-dockerman
opkg install luci-i18n-dockerman-zh-cn

opkg install luci-app-vlmcsd
opkg install luci-i18n-vlmcsd-zh-cn

opkg install luci-app-ddns
opkg install luci-i18n-ddns-zh-cn

opkg install luci-app-upnp
opkg install luci-i18n-upnp-zh-cn
```

