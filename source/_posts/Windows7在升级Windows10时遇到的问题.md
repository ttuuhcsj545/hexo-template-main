---
title: Windows7在升级Windows10时遇到的问题
date: 2025-07-21 16:10:00
updated: 2025-07-21 16:38:00
tags: [Windows10,升级]
description: Windows7在升级Windows10时遇到的问题,出现0x80072f8f-0x20000的解决方案,启动安装程序时出现问题,解决方案
index_img: https://img.tianzhihao.dpdns.org/Windows7在升级Windows10时遇到的问题/images.webp
---
##  Windows7在升级Windows10时出现0x80072f8f-0x20000
### 解决方案-1
下载地址：https://download.microsoft.com/download/0/6/5/0658B1A7-6D2E-474F-BC2C-D69E5B9E9A68/MicrosoftEasyFix51044.msi  
[点击下载](https://download.microsoft.com/download/0/6/5/0658B1A7-6D2E-474F-BC2C-D69E5B9E9A68/MicrosoftEasyFix51044.msi)  
安装 MicrosoftEasyFix51044.msi，安装后重启就能正常的运行升级工具了
![tupina](https://img.tianzhihao.dpdns.org/Windows7在升级Windows10时遇到的问题/屏幕截图%202025-07-21%20161448.webp)  
### 解决方案-2
首先电脑键盘按win+R键调出运行框，输入Regedit进入注册表编辑器，然后
按照下面的路径(32位win7系统和64位win7系统路径有一点点小区别)依次找到  
以下为64位win7路径：
```
HKEY_LOCAL_MACHINE

SOFTWARE_WOW6432NODE_MICROSOFT_WINDOWS_

CURRENTVERSION_INTERNET SETTINGS_WINHTTP
```
以下是32位win7系统路径：
```
HKEY_LOCAL_MACHINE

SOFTWARE_MICROSOFT_WINDOWS

CURRENTVERSION_INTERNET SETTINGS_WINHTTP
```
右键新建DWORD32位值，名称设置为

```DefaultSecureProtocols```

设置好后修改十六位数值为```a00```

重启

##  Windows7在升级Windows10时出现启动安装程序时出现问题
### 解决办法
1、检查WindowsModulesInstaller服务：按下`Win+X`打开开始菜单，选择“运行”。输入`services.msc`并点击确定进入服务控制面板。找到`WindowsModulesInstaller`服务。如果该服务被禁用，双击打开属性，选择启动类型为“自动”，然后重启计算机。  

2、确保使用最新版本的Windows安装程序：如果不是最新版本，尝试下载更新的版本。检查电脑是否满足Windows的最低系统要求。如果不满足，则无法安装Windows。  

3、暂时禁用防病毒软件和防火墙：有时防病毒软件和防火墙可能会阻止安装程序的正常运行。  

4、使用官方Windows10ISO镜像：从Microsoft官方网站下载Windows10ISO镜像文件，并使用刻录工具将其刻录到USB设备或DVD上。使用该设备进行安装。  

5、使用故障排除程序：如果以上方法都无法解决问题，可以尝试使用Windows10自带的故障排除程序修复问题。在Windows10设置中搜索“故障排除”即可找到该功能。  

6、联系Microsoft官方客服：如果问题依然无法解决，建议联系Microsoft官方客服进行进一步的技术支持和帮助。
