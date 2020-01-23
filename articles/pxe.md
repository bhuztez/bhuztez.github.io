Title: 基于NetworkManager配置PXE Server
Date: 2017-06-11
Slug: pxe-with-networkmanager
Tag: PXE
Tag: NetworkManager

现在常见的Linux发行版，桌面网络都是用NetworkManager管的。Fedora Installation Guide里的方法[^#]并不适用。

[^#]: https://docs.fedoraproject.org/en-US/Fedora/25/html/Installation_Guide/chap-pxe-server-setup.html

<!-- more -->

在NetworkManager里的IPv4 Settings设置Method为Shared to Other Computers，就会启动dnsmasq，里面已经有DHCP server了，所以并不需要额外运行dhcpd。只需要在`/etc/NetworkManager/dnsmasq-shared.d/`下添加一个配置文件就可以了

    server=127.0.0.1
    dhcp-match=set:efi-x86_64,option:client-arch,7
    dhcp-boot=tag:efi-x86_64,shim.efi

而在`/var/lib/tftpboot`目录下，应该使用这样的目录结构，不然根本就找不到grub.cfg，并且文件复制进去之后要restorecon，不然SELinux会阻止tftp-server读取里面的文件。

    EFI/
      fedora/
        grub.cfg
    f25/
      vmlinuz
      initrd.img
    shim.efi
    grubx64.efi
