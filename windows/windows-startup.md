# Windows程序自启动位置





### 一、在“启动”文件夹中寻找

古早系统（Win 2000/XP）的`启动`文件夹一般位于`系统盘符/Documents and Settings/用户名/开始菜单/程序/启动/`  目录 或`系统盘符/WINDOWS/Start Menu/Programs/启动/`目录。通过快捷方式的属性可以查出程序所在的位置。

比较新的系统如Win10，全局的在：`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup`, 用户的：`C:\Users\用户名\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`。

WinXP和Win7的“开始菜单”路径也不唯一，甚至比Win8和Win10还要多一个路径：`C:\Users\用户名\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\Start Menu`。

### 二、从自动批处理文件中寻找

在Win 98中，Autoexec.bat和Winstart.bat文件中的程序在开机时自动执行；而在Win Me/2000/XP/2003中，这两个批处理文件默认不被执行。



### 三、从系统配置文件中寻找

在有些系统配置文件中也可以找到自启动程序的踪迹，如Config.sys、Win.ini、System.ini、Wininit.ini和Msdos.sys等。

####  1.WIN.INI启动： 
启动位置（file.exe为要启动的[文件](http://www.myfaq.com.cn/Soft/Tools/File/index.html)名称）： 

```
[windows] 
load=file.exe 
run=file.exe 
```

注意：load=与run=的区别在于：通过load=运行文件会在后台运行（最小化）；而通过run=来运行，则[文件](http://www.myfaq.com.cn/Soft/Tools/File/index.html)是在默认状态下被运行的。 

####  2.SYSTEM.INI启动： 
启动位置（file.exe为要启动的文件名称）： 
默认为： 

```
[boot] 
Shell=Explorer.exe 
```

可启动文件后为： 

```
[boot] 
Shell=Explorer.exe file.exe 
```

WINSTART.BAT启动： 
这是一个系统自启动的批处理文件，主要作用是处理一些需要复制、删除的任务。譬如有些软件会在安装或卸载完之后要求重新启动，就可以利用这个复制和删除一些文件来达到完成任务的目的。如： 

```
“@if exist C:WINDOWSTEMPPROC.BAT call C:WINDOWSTEMPPROC.BAT” 
```

这里是执行PROC.BAT文件的命令； 

```
“call filename.exe > nul” 
```

这里是去除任何在屏幕上的输出。 
值得注意的是WinStart.BAT文件在某种意义上有和AUTOEXEC.BAT一样的作用。如果巧妙安排完全可以达到修改系统的目的！

### 四、通过“系统配置实用程序”寻找
在“开始→运行”中键入“msconfig.exe”启动“系统配置实用程序”，进入“启动”选项卡，即可查看随系统启动的程序名称和位置。

注意：Win 2000本身没有Msconfig程序，可以从Win XP/2003中提取。

### 五、从计划任务中寻找

在`控制面板`中双击“任务计划”就可以查看是否有计划任务随系统一起启动。

### 六、使用“系统信息”寻找

进入“系统信息”主界面，依次展开分支“软件环境→启动程序”，就可以在右窗格中查看自启动程序名称和位置。

### 七、使用“组策略”寻找

在Win 2000/XP/2003中，在“开始→运行”中键入“gpedit.msc”，打开“组策略”，依次展开“用户配置→管理模板→系统→登录/注销”，双击“在用户登录时运行这些程序”，单击“显示”按钮，即可查看自启动程序。

### 八、通过注册表寻找

在注册表中，可以从下列键值中查找自启动程序的名称和位置。

#### 1.Userinit键

位于“HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/WindowsNT/CurrentVersion/Winlogon/Userinit”。这个键允许指定用逗号分隔的多个程序。例如“userinit.exe,OSA.exe”(不含引号)。 

#### 2.Explorer/Run键

位于“HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/Policies/Explorer/Run”
和“HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/Policies/Explorer/Run”。

####  3.RunServicesOnce键

RunServicesOnce键用来启动服务程序，在用户登录之前启动，具体位置是:“HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/RunServicesOnce”
和“HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/RunServicesOnce”。

#### 4.RunServices键

RunServices键指定的程序在RunServicesOnce指定的程序之后运行，不过仍在用户登录之前。具体位置是：“HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/RunServices”
和“HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/ CurrentVersion/RunServices”。

#### 5.Run键

Run是自动运行程序最常用的键，位置在“HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/Run”和

“HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/Run”。

#### 6.Load键

位于“HKEY_CURRENT_USER/Software/Microsoft/WindowsNT/CurrentVersion/Windows/load”。

另外还有RunOnce、RunOnce/Setup等键。 

```
HKEY_CURRENT_USER/Software/Microsoft/WindowsNT/CurrentVersion/Windows/load
HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/Policies/Explorer/Run
HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/RunServicesOnce
HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/RunServices
HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/RunOnce/Setup
HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/RunOnce
HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/Run

HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/WindowsNT/CurrentVersion/Winlogon/Userinit
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/Policies/Explorer/Run
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/RunServicesOnce
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/RunServices
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/RunOnce/Setup
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/RunOnce
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/RunOnceEx
HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/Run


```

