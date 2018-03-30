
作用
--

	windows操作系统下,在右键菜单中添加进入cmd窗口的快捷图标.

步骤
--

	添加.reg文件
	内容如下
```
Windows Registry Editor Version 5.00

[-HKEY_CLASSES_ROOT\Directory\shell\runas]

[HKEY_CLASSES_ROOT\Directory\shell\runas]
@="Open CMD"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\shell\runas\command]
@="cmd.exe /s /k pushd \"%V\""

[-HKEY_CLASSES_ROOT\Directory\Background\shell\runas]

[HKEY_CLASSES_ROOT\Directory\Background\shell\runas]
@="Open CMD"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Directory\Background\shell\runas\command]
@="cmd.exe /s /k pushd \"%V\""

[-HKEY_CLASSES_ROOT\Drive\shell\runas]

[HKEY_CLASSES_ROOT\Drive\shell\runas]
@="Open CMD"
"HasLUAShield"=""

[HKEY_CLASSES_ROOT\Drive\shell\runas\command]
@="cmd.exe /s /k pushd \"%V\""


```
	双击文件,注入注册表即可\
	
	
# PowerShell

    直接运行powershell，即可打开PowerShell	