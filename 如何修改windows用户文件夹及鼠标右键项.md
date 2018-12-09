# win10如何删除用户文件夹（文档，视频，音乐，下载等）

### 一、`win+R`打开注册表，然后找到:
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace`

目录下:

> **下载** 对应 **{088e - - e115f}**
> **图片** 对应 **{24ad3 - - 17aa8}**
> **音乐** 对应 **{3dfdf - - cf4de}**
> **文档** 对应 **{d3162 - - a08af}**
> **视频** 对应 **{f86fa - - 67f3a}**
> **桌面** 对应 **{B4BFC - - 7C641}**
> **3D看图** 对应 **{0DB7E - - E513A}**

把这些对应项全部删除，再重新打开文件管理器，就发现它们全都没了(问题是保存文件窗口也找不到桌面选项了)。
	
另存为没有桌面的解决办法是，文件夹内依次 `查看->导航窗格->显示所有文件夹`，就会出现桌面项，然后右键`桌面项->固定到“快速访问”`，这样另存为时，就可以在快速访问中选到“桌面”选项了。

### 二、删除文件夹左侧的OneDrive项，注册表找到：

> `HKEY_USERS\S-1-5-21-855336402-1322093972-3097203920-1001\Software\Classes\CLSID\{018D5C66-4533-4307-9B53-224DE2ED1FE6}`

查看目录下的各项，看内容修改。

### 三、管理鼠标右键 Open with 。。。的目录：
> `HKEY_USERS\S-1-5-21-855336402-1322093972-3097203920-1001_Classes\*\Shell`

以 `EverEdit` 为例，

1. `Shell`目录下新建 项，命名为`EverEdit` ，
2. 右键刚新建的`EverEdit` 项，修改右边的`默认`值为`Open with EverEdit`,
3. 在`默认`下面再新建一个字符串值，命名为`icon`，修改其值为EverEdit的绝对路径`D:/Program Files/EverEdit/EverEdit.exe `.
4. 然后不出意外的话，右键一个文本文件试试吧。