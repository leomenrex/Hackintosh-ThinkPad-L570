## 版本信息
基于 Opencore 0.6.9 安装 MacOS Catalina 10.15.7 

<br />

## 截图
![screenshot](https://raw.githubusercontent.com/leomenrex/Hackintosh-ThinkPad-L570/main/screenshot1.png)

<br />

## 硬件
Lenovo ThinkPad L570 20J8，除机械硬盘外其余均为原配件
| 种类 | 型号 |
| :-----: | :-----: |
| CPU | Core i5-7200U |
| 显卡 | 核显 HD 620 |
| 内存 | 8GB DDR4 2133MHz |
| 显示屏 | 内建 1366*768 |
| 无线网卡 | Intel AC-8265 |
| 有线网卡 | Intel I-219V |
| 声卡 | Realtek ALC-293 |
| 触控板 | ALPS V8 |
| 硬盘 | Seagate HDD |
<br />

## BIOS 设置
BIOS 版本 N1XET72W（1.50）
没有提及的选项按默认
+ **Config**
    + Network > Wake On LAN **关闭**
    + Keyboard/Mouse > Fn and Ctrl Key swap **开启**
    + Keyboard/Mouse > F1–F12 as primary function **开启**
+ **Security**
    + Security Chip > Security Chip **关闭**
    + Memory Protection **关闭**
    + Virtualization > Intel (R) Virtualization Technology **开启**
    + Virtualization > Intel (R) VT-d Feature **开启**
    + I/O Port Access **按需**，这里关闭了麦克风和摄像头
    + Anti-Theft > Computrace Module Activation **关闭**
    + Secure Boot > Secure Boot **关闭**
    + Intel (R) SGX > Intel (R) SGX Control **关闭**
+ **Startup**
    + Boot 调整 USB 启动为首位
<br />

## 正常工作的部件
+ CPU 正常变频
    + 已通过 CPUFriendFriend 脚本将频率设为最低水平（EPP 为 FF，Bias 为 15），如有需要可以自己制作替换 CPUFriendDataProvider.kext
+ 核显正常驱动，支持缩放/调节亮度/夜览
+ USB 接口完成定制，支持 USB3.0
+ 合盖/电源键睡眠，开盖/电源键唤醒亮屏，已加载原生电源管理（建议将`HibernateMode`设为 0，只睡眠）
+ 声音输出正常/有线网卡正常
+ 无线网卡需要安装 [Heliport](https://github.com/OpenIntelWireless/HeliPort) 来管理 WiFi 接入，或者使用该作者的 [AirportItlwm](https://docs.oiw.workers.dev/itlwm/Installation.html#airportitlwm) 替代网卡驱动（需要安全启动）
+ 键盘音量快捷键 <kbd>Fn</kbd>+<kbd>F1</kbd>-<kbd>F3</kbd>，亮度快捷键 <kbd>Fn</kbd>+<kbd>F5</kbd>-<kbd>F6</kbd> 正常，<kbd>PrtSc</kbd> 键映射为 <kbd>F13</kbd>
+ 正确显示电池电量
<br />

## 存在的问题
+ 触控板只支持单点，不支持多点和手势
    + 自带的最新版官方 VoodooPS2Controller 无法正确识别触控板，只能支持单点；
    + 替换使用 [附加文件](https://github.com/leomenrex/Hackintosh-ThinkPad-L570/tree/main/Extra_files) 的驱动可以识别触控板，可以使用手势，但点击/按键/小红点都不能用；暂时没有找到完美的驱动
+ 键盘其余快捷键（如 <kbd>Fn</kbd>+<kbd>F7</kbd>，计算器键等）没有进行适配，可参照文末的引用文章
+ 蓝牙无驱动（我没有这个需求，需要使用蓝牙的要自行搜寻驱动）
+ 长时间睡眠唤醒后，有概率出现使用的 USB 设备被强制弹出，暂未发现重现规律
+ eDP 接口未做测试
+ 麦克风/摄像头已在 BIOS 设置关闭，也没有测试
<br />

## 参照
+ Dortania Guide 系列教程 https://dortania.github.io
+ OpenCore 中文手册 https://oc.skk.moe/
+ OC-little 项目及说明 https://github.com/daliansky/OC-little
+ 进阶 FN 键定制 https://blog.skk.moe/post/ssdt-map-fn-shortcuts
+ Dr.Hurt ALPS 触控板驱动贴 https://osxlatitude.com/forums/topic/8285-refined-alps-touchpad-driver
+ XJN 的 OC-guide https://blog.xjn819.com/post/opencore-guide.html
+ B站UP司波图的相关视频 https://space.bilibili.com/28457/video
