---
title: WindowsOfficeActivate
description: windows 激活
published: true
date: 2025-03-10T06:15:08.207Z
tags: win
editor: markdown
dateCreated: 2024-02-19T06:01:01.516Z
---

# 可能的问题
告警```你可能是盗版软件受害者```
通过office Tool plus工具设置kms主机
链接: https://pan.baidu.com/s/1ZENtawaMbC10fRiDLBtqHg 提取码: qydu 


# 搭建kms服务器
不能在同一台设备上运行kms和激活

## 直接下载运行
参考：https://blog.csdn.net/xingyu97/article/details/89381018
参考：https://zhuanlan.zhihu.com/p/355184532
下载：https://github.com/Wind4/vlmcsd/releases

Linux
```
解压
tar -zxvf binaries.tar.gz
cd binaries/Linux/intel/static

运行
./vlmcsdmulti-x64-musl-static vlmcsd
```

Windows *(推荐做成 nssm服务)*
```
vlmcsdmulti-Windows-x64.exe vlmcsd

测试连接
vlmcs-Windows-x64 [IP]
```
运行后会占用端口1688

## docker安装
docker run -d -p 1688:1688 --restart=always --name="vlmcsd" mikolatero/vlmcsd

# 激活专业版
参考：
https://zhuanlan.zhihu.com/p/152269085
https://msguides.com/microsoft-software-products/2-ways-activate-windows-10-free-without-software.html
企业版key：M7XTQ-FN8P6-TTKYV-9D4CC-J462D ，参考：https://github.com/wangji817/active-win10-EnterpriseEdition-LTSC
```
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms kms.03k.org
slmgr /ato
```

## 激活office 2015
```
cscript ospp.vbs /sethst:vpn.sibogao.cn
cscript ospp.vbs /act
cscript ospp.vbs /dstatus
```
error code 0x80070005 权限不够，以管理员权限运行


## 激活office 2019
office key:https://learn.microsoft.com/zh-cn/DeployOffice/vlactivation/gvlks?redirectedfrom=MSDN
```bat
@echo off
(cd /d "%~dp0")&&(NET FILE||(powershell start-process -FilePath '%0' -verb runas)&&(exit /B)) >NUL 2>&1
title Office 2019 Activator r/Piracy
echo Converting... & mode 40,25
(if exist "%ProgramFiles%\Microsoft Office\Office16\ospp.vbs" cd /d "%ProgramFiles%\Microsoft Office\Office16")&(if exist "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" cd /d "%ProgramFiles(x86)%\Microsoft Office\Office16")&(for /f %%x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%%x" >nul)&(for /f %%x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%%x" >nul)
cscript //nologo ospp.vbs /unpkey:6MWKP >nul&cscript //nologo ospp.vbs /inpkey:NMMKJ-6RK4F-KMJVX-8D9MJ-6MWKP >nul&set i=1
:server
if %i%==1 set KMS_Sev=vps.cxlljj.top
if %i%==2 set KMS_Sev=vps.cxlljj.top
if %i%==3 set KMS_Sev=vps.cxlljj.top
cscript //nologo ospp.vbs /sethst:%KMS_Sev% >nul
echo %KMS_Sev% & echo Activating...
cscript //nologo ospp.vbs /act | find /i "successful" && (echo Complete) || (echo Trying another KMS Server & set /a i+=1 & goto server)
pause >nul
exit
```
离线安装后 office 提示“很抱歉，此功能看似已中断” 解决办法
链接：https://zhuanlan.zhihu.com/p/324859213

>打开注册表，找到以下键值：计算机\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\16.0\Word\Options
>右侧新建32位DWORD值，取名为NoReReg，并输入数值为1 并确认，关闭注册表编辑器，重新打开Word 即可。

## 激活Office2016
```
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\ProPlusVL_KMS_Client-ul.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\ProPlusVL_KMS_Client-ppd.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\ProPlusVL_KMS_Client-ul-oob.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\ProPlusVL_MAK-pl.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\ProPlusVL_MAK-ppd.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\ProPlusVL_MAK-ul-oob.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\roPlusVL_MAK-ul-phn.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\client-issuance-bridge-office.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\client-issuance-root-bridge-test.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\client-issuance-ul-oob.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\client-issuance-ul.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\client-issuance-stil.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\client-issuance-root.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\pkeyconfig-office-client15.xrm-ms"
cscript "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" /inslic:"%ProgramFiles(x86)%\Microsoft Office\root\Licenses16\pkeyconfig-office.xrm-ms"

cscript ospp.vbs /inpkey:XQNVK-8JYDB-WJ9W3-YJ8YR-WFG99
cscript ospp.vbs /sethst:vps.cxlljj.top
cscript ospp.vbs /act
```

## 激活Visio2016
```
# 进入Office安装目录，64位安装目录为：C:\Program Files\Microsoft Office\Office16，32位安装目录为：C:\Program Files (x86)\Microsoft Office\Office16
# 与激活Office不同的是，在激活之前需要运行以下三条命令安装证书：
cscript OSPP.VBS /inslic:"..\root\Licenses16\VisioProVL_KMS_Client-ppd.xrm-ms"
cscript OSPP.VBS /inslic:"..\root\Licenses16\VisioProVL_KMS_Client-ul.xrm-ms"
cscript OSPP.VBS /inslic:"..\root\Licenses16\VisioProVL_KMS_Client-ul-oob.xrm-ms"

cscript ospp.vbs /inpkey:PD3PC-RHNGV-FXJ29-8JK7D-RJRJK
cscript ospp.vbs /sethst:vps.cxlljj.top
cscript ospp.vbs /act
```
