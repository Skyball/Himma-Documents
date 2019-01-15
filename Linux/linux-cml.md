### ps

```linux
ps -ef|grep jetty
```

### netstat 

> 使用命令：netstat –apn
> 发现8080端口被PID为9658的Java进程占用。
>
> 进一步使用命令：ps -aux | grep java，或者直接：ps -aux | grep pid 查看

```
netstat -apn|grep 8083
```

### nohup

```
nohup java  -jar start.jar &
```

### cp 

```
cp -r /usr/kk  /usr/install
```

### rm

> mv命令来为文件或目录改名或将文件由一个目录移入另一个目录中。
> 格式
> mv [options] 源文件或目录 目标文件或目录。
> 主要参数[options]
> －i：交互方式操作。如果mv操作将导致对已存在的目标文件的覆盖，此时系统询问是否重写，要求用户回答”y”或”n”，这样可以避免误覆盖文件。
>
> －f：禁止交互操作。mv操作要覆盖某个已有的目标文件时不给任何指示，指定此参数后i参数将不再起作用。
> mv new.c new0.c     重命名文件（cp时同理，也可以重命名）
>
> -r开关：递归地删除子目录和子目录中的文件
>
> -f开关：强制删除，不再一一向用户提示确认
>
> rm -rf * 删除当前目录下的所有文件。

```
rm -rf targetFolder
```

### df -h

**df命令可以显示目前所有文件系统的可用空间及使用情形**,    参数 -h 表示使用「Human-readable」的输出，也就是在档案系统大小使用 GB、MB 等易读的格式。

