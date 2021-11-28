# win删除被占用的文件

Sysinternals Suite是一个工具程序集

**执行工具**
.\handle [文件名]
```cmd
.\handle gradle-7.1-all
```

**结束进程**
Taskkill /pid \[进程码] -t(结束该进程) -f(强制结束该进程以及所有子进程)
```cmd
taskkill /pid 16172 -t
taskkill /pid 16172 -f
```