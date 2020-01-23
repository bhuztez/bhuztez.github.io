Title: 又双叒叕造了一个静态网页生成工具
Slug: yet-another-static-site-generator
Date: 2020-01-22
Tag: elaphure

早期所谓的共享空间，就只有个FTP供你上传静态网页。后来随着PHP成为了最好
的编程语言，很多之前很火的静态网页生成工具都销声匿迹了。谁又能料到，
2008年GitHub推出了Pages功能，静态网页生成工具卷土重来。时至今日，据
[Static Site Generators](https://staticsitegenerators.net)的不完全统计，
已经有460了。

<!-- more -->

虽然有这么多，然而换来换去，竟然找不到一个比较好用的，都有这样或者那样
的问题。我想我的要求并不高，也就这么几条

* 文件修改之后，在本地预览是可以立即看到变化的，而不是需要重新生成所有HTML，或者页面只有一部分会变
* 方便配置，而不是随便加点功能都要写个插件

怪不得轮子哥要说Shopping is hard, lemme reinvent the wheel.

曾有一段时间不自量力的认为，可以写一个增量更新的工具来解决这个问题。然
而花了好久也没写出来。后来反思了一下，重复发明轮子的重点是重复而不是发
明。

既然如此，直接用生成动态网页的库就好了，需要补的仅仅是

* 怎么找出URL routing里一条规则所有可能的参数
* 文件发生变化时自动更新数据库

前者只需要要求每个view都提供find_all。而后者可以用
[watchdog](https://pypi.org/project/watchdog/)办到。

因为sqlite早就支持JSON了，所以每个文件的metadata都以JSON格式存到sqlite
里。可是Python自带的sqlite版本要么太老，要么没打开JSON1，所以最后花了
很多时间在[[sqlite3ct]]上。
