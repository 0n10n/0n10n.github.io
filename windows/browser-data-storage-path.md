# 浏览器敏感数据存放位置

## Google chrome位置

在 Windows 10 和Windows 11里，Chrome浏览器的cookies信息，都存放在以下目录内的Cookies文件里（SQLite格式）：

C:\Users\Your_User_Name\AppData\Local\Google\Chrome\User Data\Default\Network

更通用的写法是：

%LOCALAPPDATA%\Google\Chrome\User Data\Default\Network

## Firefox 位置

## Where does Firefox store cookies in Windows?

Firefox存放cookie的文件叫`cookies.sqlite`。首先到以下目录：

%APPDATA%\Mozilla\Firefox\Profiles

也就是类似这个目录：

C:\Users\Your_User_Name\AppData\Roaming\Mozilla\Firefox\Profiles

在上面目录里，有个名为`8位随机字母数字.default-release`的子目录，*cookies.sqlite*文件就在这里。

## Edge位置

Edge浏览器和Chrome类似， 也存放在`Cookies`文件里。具体位置：

%LOCALAPPDATA%\Microsoft\Edge\User Data\Default\Network

也就是类似这样

C:\Users\Your_User_Name\AppData\Local\Microsoft\Edge\User Data\Default\Network

## 工具

- SharpChromium