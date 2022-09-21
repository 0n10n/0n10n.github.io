## Win11 右键老版菜单

1. 注册表路径:HKEY_CURRENT_USER\SOFTWARE\CLASSES\CLSID
2. 右键点击CLSID项，新建一个项，名为{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}
3. 右键点击新创建的项，再新建一个项，名为InprocServer32.
4. 选择新创建的项，双击右侧的默认条目，直接按下回车键.

## WSL与物理机通信,添加防火墙规则

```
PS C:\WINDOWS\system32> New-NetFirewallRule -DisplayName "WSL" -Direction Inbound -InterfaceAlias "vEthernet (WSL)" -Action Allow
```