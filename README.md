# Lenovo 天逸 510S Mini Hackintosh

![release version](https://img.shields.io/github/v/release/daliansky/Lenovo-TianYi-510S-Mini-Hackintosh?style=for-the-badge) 

[![OpenCore version](https://img.shields.io/badge/OpenCore-0.9.5-informational.svg)![MacOS version](https://img.shields.io/badge/Sonoma-14.0-informational.svg)](https://github.com/acidanthera/OpenCorePkg)![MacOS version](https://img.shields.io/badge/Ventura-13.6-informational.svg)![MacOS version](https://img.shields.io/badge/Monterey-12.6.1%2021G115-informational.svg)

## 电脑配置

|   规格   |                           详细信息                           |
| :------: | :----------------------------------------------------------: |
| 电脑型号 |                  联想Lenovo 天逸 510S Mini                   |
| 操作系统 |     macOS `Sonoma` / `Ventura` / `Monterey` / `Big Sur`      |
|  处理器  |                    英特尔 酷睿 i5 - 10400                    |
|   内存   |                             16GB                             |
|  硬盘1   |               SKhynix 256GB，已更换为WD SN750                |
|  硬盘2   |                       ST2000LM007 2TB                        |
|   显卡   |                  Intel HD Graphics CFL CRB                   |
|  显示器  |                              无                              |
|   声卡   |                        Realtek ALC235                        |
|   网卡   | Intel AX201，已更换为[BCM94360Z4](https://blog.daliansky.net/uploads/WeChatandShop.png) |

## 更新日志

- 6-12-2024
  - 更新 `IOSkywalkFamily.kext` 到 `v1.1.0`
  - `Sonoma` 如果想更新到 `14.4` 请务必先更新 `EFI` ，然后再安装 [OCLP](https://pan.daliansky.net/APPS/OCLP/OCLP.md)，重启后，再升级到 `14.4` 否则会出现 `WIFI` 无法启用的问题
- 10-20-2023
  - 更新 `OpenCore` 到 `v0.9.5`
  - 提供对 `Sonoma` 的初步支持
  - 博通网卡需要使用 `OCLP` 打补丁，附：[教程链接](https://blog.daliansky.net/OCLP.html)
- 11-4-2022
  - `v2.4.0`
  - OpenCore `v0.8.5` Release
  - 支持 `Ventura`
- 2-14-2022
  - `v2.3.0`
  - OpenCore `v0.7.8` Release
- 10-28-2021
  - `v2.2.0`
  - OpenCore `v0.7.5` Release
  - 更新对于 `Monterey` 的安装使用
  - 修复声卡驱动，完美支持 `Monterey` 下使用
- 8-13-2021 `v2.1.0`
  - OpenCore `v0.7.1` Release
  - 修复`HDMI`紫屏
  - 其它驱动常规更新
- 5-13-2021 `v2.0.0`
  - OpenCore `v0.6.9` Release
  - USB端口定制，适配Big Sur 11.3.x
  - 修复DP 音频输出
- 1-25-2021 `v1.5.0`
  - OpenCore `v0.6.6` 开发版
  - Release `v1.5.0`
  - 更新了新的[BCM94360Z4](https://blog.daliansky.net/uploads/WeChatandShop.png)驱动
- 1-5-2021
  - OpenCore `v0.6.5`
  - Release `v1.4.0`
- 12-25-2020
  - 修复`HDMI`睡眠唤醒后的黑屏问题，感谢群友@恩-和气生财的反馈
  - Release `v1.3.0`
- 12-24-2020
  - OpenCore `v0.6.4`
  - Release `v1.2.0`
- 11-18-2020
  - OpenCore `v0.6.3`
  - 精简无用的驱动
- 10-26-2020
  - 修复`HDMI`紫屏问题，完美支持`DP+HDMI`双屏显示
- 10-13-2020
  - OpenCore `v0.6.2`
  - 支持`Big Sur` / `Catalina`安装使用
  - 支持`DP` + `HDMI`双显
  - 声卡驱动完美，包括显示器音频输出功能正常
  - 网卡驱动默认为：`DW1820A`，如果使用`INTEL`无线网卡请在配置文件中勾选三个驱动

### 设置`BIOS`

- 安全菜单：
  
  - 安全启动 -> `关闭`  (*Disable Secure Boot*)
  
- 高级菜单：
  
  - CPU菜单：`CFG Lock` -> `关闭` (*Disabling CFG Lock*)【相关BIOS请进群获取】
  
  ![BIOS-CFG-LOCK](./ScreenShots/BIOS-CFG-LOCK.png)
  
- 设备：
  - 显示设备
    - 预指派内存大小：`64MB` (*DVMT* pre-allocated memory)
  
  ![BIOS-DVMT](./ScreenShots/BIOS-DVMT.png)
  
  - ATA设备菜单：
    - `配置SATA为` -> `AHCI`
  
- 其它参数默认即可

- `BIOS`进QQ群里取

## 备注：

关于更新`EFI`后第一次出现的卡在`SMCSuperIO`的问题

- 请执行重启或者`Reset NVRAM`的操作即可

关于`HDMI`显示输出：

如果你的显示器没有`DP`接口，那么可以考虑购买一条`DP`转`HDMI`的线连接上就好了，也省得看下文了。

- 小兵在测试的时候发现质量差的，版本低的`HDMI`线材是无法正确识别并点亮`HDMI`的显示输出。这个问题对小兵造成了很大的困扰，折腾了好些天。在跟因为黑苹果而结缘的法师的提醒下，他无偿赞助了我一根支持`HDMI` `v2.1` 支持到`8K@60Hz` / `4K@120Hz`的线材，到手后直接点亮`HDMI`显示器，估计支持`v2.0` `4K@60Hz`的线材也能正常使用，低于`v2.0`版本的可能就需要注入`EDID`值才能显示输出

  线材购买链接：https://item.jd.com/100008665276.html

- 配置文件中，在`DeviceProperties` - `PciRoot(0x0)/Pci(0x2,0x0)`里，我添加了三行以`#`开头的注释信息，其中第一行为备注，内容为：

  ```xml
  #0备注：如果想单独使用HDMI输出显示，请启用#AAPL0x这两行关于显示器的注入信息，也可以替换成自己的显示器的EDID值
  ```

  后面的两行`#AAPL0x`开头的为两台显示器的注入信息，它可以保证在普通线材连接`HDMI`接口的情况下能正确点亮显示器完成安装，使用的时候需要将`#AAPL0x`中的`#`移除掉以使其数值生效

- `EDID`值可以注入你自己的显示器，这样可以保证显示输出正常工作，至于如何提取`EDID`值，请移步博客或者通过谷歌搜索寻找答案

## 截屏

![S510Mini](./ScreenShots/S510Mini.jpg)

![ZSH](./ScreenShots/ZSH.png)

![Displays](./ScreenShots/Displays.png)

![Hackintool](./ScreenShots/Dual_Monitor.png)

![Sounds](./ScreenShots/Sounds.png)

![Hackintool_Misc](./ScreenShots/Hackintool_Misc.png)

![Hackintool_Audio](./ScreenShots/Hackintool_Audio.png)

![Hackintool_USBMAP](./ScreenShots/Hackintool_USBMAP.png)

![Memory](./ScreenShots/Memory.png)

![BigSur](./ScreenShots/BigSur.png)

## QQ交流群：

942112153 [天逸510s Mini黑苹果交流群](https://qm.qq.com/cgi-bin/qm/qr?k=N5cjw5ksrnmk-RMQ4fPCOo5D_Dxiu47B&jump_from=webapi) 1000人群 非专用机型请勿加入

![WeChatandShop](ScreenShots/WeChatandShop.png)

## EFI下载

https://github.com/daliansky/Lenovo-TianYi-510S-Mini-Hackintosh/releases/

