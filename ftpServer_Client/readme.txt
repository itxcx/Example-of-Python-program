1.客户端登录ftp服务器

在这个功能里，需要用户输入账号密码，然后通过sock发送给服务端，服务端收到后，从MySQL数据库中判断是否存在该用户，如果存在，那么提取该用户的密码，将密码进行核对。

账号密码核对成功后，客户端直接进入命令行模式，需要有指定格式光标。

2.查看文件列表信息

在这个功能里，客户端只需要将命令通过sock传输给服务端，服务端再调用python自带的os模块，就可以执行ls等命令，服务端再将信息输出通过sock传输给客户端，客户端再进行展示即可。

3.切换目录

在这个功能里，可以使用cd命令进行目录切换，但是并不是随意切换，而是只能切换到家目录，或者文件上传的目录，或者文件下载的目录。其他的目录即使输入切换命令，也会提示错误。
4.文件上传

在这个功能里，限定用户只能从自己的家目录将文件上传到服务端的上。在服务端上，指定某个路径给客户端进行文件上传。
5.文件下载

这个功能也是限制用户只允许下载服务端上指定的目录下的文件，并将下载的文件保存在自己的家目录中，不能保存在其他的地方。
6.文件删除

文件删除功能并没有什么特别的，客户端需要做的是将文件列表传输给服务端，服务端收到列表后，调用os等python模块，或者commands模块执行文件删除命令即可。
7.文件传输进度条

实现文件传输提示百分比进度条。