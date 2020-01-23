Title: sqlite3ct
Tag: project

因为[[elaphure]]用到了sqlite的JSON1扩展，而Python自带的sqlite版本要么
太老，要么没开启JSON1。编译Python也挺麻烦的。所以用
[ctypes](https://docs.python.org/3/library/ctypes.html)和Python里的
sqlite3一模一样包了一遍sqlite的API。在Windows下，假设已经用choco安装了
最新版的sqlite。
