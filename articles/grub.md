Title: 在Fedora上继续使用GRUB
Date: 2014-10-19
Slug: keep-grub-on-fedora
Tag: Fedora
Tag: GRUB

Fedora从某个版本开始默认使用GRUB2了。实在搞不明白无比复杂的GRUB2，还是继续用GRUB吧。可是没过多久fedora-logos里都不带GRUB的背景图了，只好果断抛弃，用generic-logos。另外还在`/etc/yum.conf`里把GRUB2什么的统统禁掉，免得distro-sync完了以后GRUB没了。

<!-- more -->

    exclude=grub2 grub-efi grub2-efi
