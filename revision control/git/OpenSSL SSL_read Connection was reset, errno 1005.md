# OpenSSL SSL_read: Connection was reset, errno 1005

[草稿]

> 首先，造成这个错误很有可能是网络不稳定，连接超时导致的，
如果再次尝试后依然报错，可以执行下面的命令

打开Git命令页面，执行git命令脚本：修改设置，解除ssl验证

```bash
git config --global http.sslVerify "false"
```