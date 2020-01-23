Title: 在Fedora 12上用WINE运行QQ 2009
Date: 2010-12-09
Slug: qq-2009-on-fedora-12
Tag: Fedora
Tag: QQ

QQ 2009以前的版本，用从网上找来的方法，把QQ用WINE运行起来并没有什么问题。自从QQ 2009开始，出现了一个问题，一点输入密码的框程序就会崩溃，也就是完全不能登录。

<!-- more -->

首先用winetricks安装必要的库`winetricks gdiplus flash ie6 msxml3 riched20 riched30 vcrun6 vcrun2005`。字体问题，在`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\FontSubstitutes`下，把`MS Shell Dlg`，`MS Shell Dlg 2`以及`Tahoma`都设置变成`SimSun`，并把`simsun.ttc`放到`WINEPREFIX/drive_c/windows/Fonts/`目录下。

干净安装好第一次运行，密码框并不会崩溃。发现是因为`Bin/tssafeedit.dat`更新了之后才会崩溃的，于是可以把原始文件保存一下，运行完了再替换回去，这样密码框就不会崩溃了。同时QQ自动更新的那个框是运行`Bin/auclt.exe`弹出来的，直接把这个文件删了，就不会了。

写了个脚本，来自动执行上面这些步骤

    :::console
    $ wget 'https://github.com/bhuztez/configs-and-scripts/raw/master/fedora-wine-qq.sh'
    $ chmod u+x fedora-wine-qq.sh
    $ ./fedora-wine-qq.sh
